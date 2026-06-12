---
title: "Autostart won't work"
date: 2019-12-27
forum: General Help
---

### Post by timswait on 2019-12-27
I've got a project setting up a datalogger for a home automation project. It's an ESP32 board running Micropython that sends MQTT messages back over the WiFi to save on the computer. I've managed to get it all working, I now simply need to start a Python script running on the computer to grab the MQTT messages. I can run it from terminal and it works perfectly. I assumed it would be trivial to get it to automatically run at startup so I don't have to type it in every time I switch the computer on, but I've spend hours on it and it still won't do it!! Things I've tried:
1. Using the Autostart GUI in System Settings (I'm on Kubuntu 18.04) to run the command "python /home/rosebank/datalogger/datalogger_server.py"
2. Writing a .sh file containing just the command "python /home/rosebank/datalogger/datalogger_server.py", making it executable and using the Autostart GUI to run that script file
3. Creating a .desktop file in ~/.config/autostart following these instructions: [https://stackoverflow.com/questions/24518522/run-python-script-at-startup-in-ubuntu/25805612#25805612](https://stackoverflow.com/questions/24518522/run-python-script-at-startup-in-ubuntu/25805612#25805612) with the Python command
4. As above but running the .sh script file
5. Copying the .desktop file from above into /etc/xdg/autostart
6. Setting 60 second delay on X-GNOME-Autostart-Delay in case the MQTT broker wasn't already running
7. creating a .conf file and putting in etc/init
8. Copying .py file into /bin and adding "@reboot python /bin/datalogger_server.py &" to the bottom of the crontab file

Literally nothing I try will make this script run!! I simply can't understand how it's this difficult, as I say all I need to do it type the command into Terminal after booting up and it works, so why can I not make it work automatically?!

---

### Post by vanadium on 2019-12-29
X-GNOME-Autostart-Delay may work under the Gnome Desktop environment, but you tell us you use Kubuntu. You can introduce a desktop-agnostic delay in the .desktop file you use in .config/autostart with the "sleep" command, as following:
```

Exec=sh -c "sleep 3 && <yourcommand>"

```
This would introduce a delay of 3 seconds before the second command is executed.

---

