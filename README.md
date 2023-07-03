# local-wifi-windows10
The code provided is written in Python and is used to retrieve the Wi-Fi profiles and passwords stored on a Windows computer 


##HOW TO RUN
:white_square_button:Open up your favourite terminal(cmd,powershell)
:white_square_button:"cd" to the directory where the python file is downloaded
:white_square_button:run the command:
```python
python win-10_wifi.py
```


##Here's a breakdown of how the code works::wavy_dash:

:small_blue_diamond:It imports the necessary modules (subprocess and re) for executing shell commands and performing regular expression operations, respectively.

:small_blue_diamond:The subprocess.run function is used to run the command netsh wlan show profiles and capture the output. The capture_output = True argument ensures that the output is captured and made available.

:small_blue_diamond:The captured output is then decoded into a string.

:small_blue_diamond:The regular expression re.findall("All User Profile : (.*)\r", command_output) is used to extract the Wi-Fi profile names from the command output. The findall function returns a list of all matched profile names.

:small_blue_diamond:An empty list wifi_list is created to store the Wi-Fi profiles and passwords.

:small_blue_diamond:If there are profile names (len(profile_names) != 0), the code iterates over each profile name.

:small_blue_diamond:For each profile name, a dictionary wifi_profile is created to store the profile's SSID (Wi-Fi name) and password (if it exists).

:small_blue_diamond:The netsh wlan show profile <profile_name> command is executed to retrieve the profile information, which is then captured and decoded.

:small_blue_diamond:If the profile information indicates that the Wi-Fi network has no security key (i.e., "Security key : Absent"), the loop continues to the next profile without adding it to the wifi_list.

:small_blue_diamond:If the Wi-Fi network has a security key, the SSID is added to the wifi_profile dictionary.

:small_blue_diamond:The netsh wlan show profile <profile_name> key=clear command is executed to retrieve the clear text password for the Wi-Fi network.

:small_blue_diamond:The captured output is searched using the regular expression re.search("Key Content : (.*)\r", profile_info_pass) to extract the password (if it exists).

:small_blue_diamond:If the password is None, it means that the network has no password. Otherwise, the password is added to the wifi_profile dictionary.

:small_blue_diamond:Finally, the wifi_profile dictionary is appended to the wifi_list.

:small_blue_diamond:The wifi_list is printed to display each Wi-Fi profile and its corresponding password (if available).

:red_circle:Note that to execute this code successfully, you need to have the necessary permissions and be running it on a Windows computer with the netsh command-line tool available.

Please let me know if you have any further questions!


