---
title: "Cron job question about starting programs"
date: 2023-02-19
forum: General Help
---

### Post by stirgejr on 2023-02-19
Good morning (where I am anyway),

I started fiddling around recently with cron jobs. Based on the plethora of tutorials online, I was able to get them to run without issue. The problem I'm having is that I want the job to open and bring up an application. I have a python script that creates/edits a text file and then opens it in VS Code. On Windows, the task scheduler ran the python job and opened the file in VS Code as expected. When I set up the cron job on my unix machine, it runs just fine, but VS Code stays hidden under all the other apps. The scripted text gets written to file, so the python code is running, but the os.system(<command string to open VS Code>) call doesn't do anything.

I have since also tried running it as a bash script, then running it as a bash script that outputs the command to another bash script and runs that, outputting the path to the desired text file in another text file and having the bash script read that as a variable after executing the python and trying to run the code -g file_path command from there. I also tried setting VS Code as my default for txt files, and then run xdg-open on the text file. Still nada. In each case, the code runs fine and adds the desired text to file, but never opens the actual application for me. I'm guessing maybe this is a perms thing with cron jobs or something? Not sure, still fairly new to fully living on a Unix machine (converted my desktop and tablet to Ubuntu about a month ago, but had previously fiddled around in Unix here and there, as well as operated in bash terminals on windows for git etc.. for a while). Any advice on how to make that happen, or if it's possible, would be appreciated.

Thanks

---

### Post by yancek on 2023-02-19
Start by posting the actual entry in cron.  One of the most common errors users make is not having the full path to the script(s) to run in cron for that particular user.  Best to have simple entries in cron pointing to a script in the user $PATH.

---

### Post by Impavidus on 2023-02-19
Cron jobs run in a very limited environment. To open a window, an applications needs some environment variables to tell it where it can contact the window manager to get a window, and those environment variables aren't defined by cron. This makes sense: cron jobs often run while the owner of the process isn't logged in, or logged in, but only by command line, or logged in using a different graphical shell. This makes it pretty hard to have a cron job open a window. It first has to make sure the user is actually logged in and has a GUI running, then it has to extract the environment variables for that GUI somewhere from the /proc pseudofilesystem, then it can open a window. Cron was designed to run automatically, without user interaction, not to start interactive applications.

If you want to start GUI applications automatically, it's best to use the session settings of your desktop environment.

---

### Post by stirgejr on 2023-02-19
> **yancek said:**
> Start by posting the actual entry in cron.  One of the most common errors users make is not having the full path to the script(s) to run in cron for that particular user.  Best to have simple entries in cron pointing to a script in the user $PATH.

I'm on my phone now (and so don't have my Cron syntax), but I made sure to use the full explicit path for everything. I'd already read online tutorials etc.. recommending that. The python executes, so there's no trouble with the job itself running and finding the scripts. Just that it wouldn't open vscode. But I think impavidus is on point about what the issue is

---

### Post by stirgejr on 2023-02-19
> **Impavidus said:**
> Cron jobs run in a very limited environment. To open a window, an applications needs some environment variables to tell it where it can contact the window manager to get a window, and those environment variables aren't defined by cron. This makes sense: cron jobs often run while the owner of the process isn't logged in, or logged in, but only by command line, or logged in using a different graphical shell. This makes it pretty hard to have a cron job open a window. It first has to make sure the user is actually logged in and has a GUI running, then it has to extract the environment variables for that GUI somewhere from the /proc pseudofilesystem, then it can open a window. Cron was designed to run automatically, without user interaction, not to start interactive applications.

If you want to start GUI applications automatically, it's best to use the session settings of your desktop environment.

Ah, interesting. I knew it was more limited, didn't know the details. Yeah that's probably exactly it. Before I go run off to Google myself, do you know of any efficient ways to execute what I'm going for? I.e. schedule a script to run every hour that opens a text file in vscode (or any other editor)?

Edit: preferably without having to download anything external. It's part of an app I'm working on, and I'd prefer to limit the amount of dependencies I need to make it work

---

### Post by TheFu on 2023-02-19
Cron is meant for batch processing, not interactive stuff.  Output should be to and from files.  

If you want to have something happen periodically, cron is the wrong tool.  I know that **alarm-clock-applet** [https://alarm-clock-applet.github.io/](https://alarm-clock-applet.github.io/) does support running any external programs at specific times or you could write a tiny script to do it has you like with a sleep command between runs. That applet is in the repos - or it was.  I think the really old **plan** X/Windows tool does as well. I used it in the mid-1990s for reminders.

```
while (1){
  run some program  &
  sleep 1h
}

```
You could have that script initially called from the DE startup settings.  [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)

So, I looked to install the alarm-clock-applet on my new Mint system (based on 22.04) and found it wasn't in the repos for 22.04 or 20.04 anymore. They  have a PPA and that does have it.  Just follow the instructions.  In typical fashion, the new version has simplified the interface to remove the clear text + icons that was there previously. It is very slow to start now - about 10-15 seconds. Probably related to the GTK+ version change.  Newer isn't always better, I'm sad to say. Still, having an alarm/schedule system is something I've built into my workflows for decades.

---

### Post by Impavidus on 2023-02-19
FYI: I do use cron to switch my wallpaper hourly. The script first checks to see if I'm running xfce4-session (I'm on Xubuntu), then it looks in the /proc system to find the DBUS_SESSION_BUS_ADDRESS environment variable (it's in the environment of xfce4-session), which it needs to contact xfconf-query, which is the command line tool to set the wallpaper on Xubuntu. So not as simple as you might think.

---

### Post by stirgejr on 2023-02-20
Interesting stuff from everyone. Yeah I had just reached fro cron jobs since that seemed like the equivalent to Windows' task scheduler. I'm glad I asked before I wasted any more time on that route lol. Appreciate all the extra information!

---

### Post by Holger_Gehrke on 2023-02-20
@impavidus: unless you have some unusual requirements for your wallpapers (like specific wallpapers at specific times or freshly generated images) there's no need to make it that complicated since XFCE has a built-in wallpaper changer. Just open the desktop settings, set the folder with your images and put a checkmark at the option to 'Change the background' and set the time.

Holger

---

### Post by TheFu on 2023-02-20
> **Impavidus said:**
> FYI: I do use cron to switch my wallpaper hourly. The script first checks to see if I'm running xfce4-session (I'm on Xubuntu), then it looks in the /proc system to find the DBUS_SESSION_BUS_ADDRESS environment variable (it's in the environment of xfce4-session), which it needs to contact xfconf-query, which is the command line tool to set the wallpaper on Xubuntu. So not as simple as you might think.

If you set the DISPLAY correct, it will work under normal X11. I have no idea is Wayland allows it or if new X11 (20.04+) allow it.
Regardless, that doesn't make it a good idea.

---

### Post by Impavidus on 2023-02-20
> **Holger_Gehrke said:**
> @impavidus: unless you have some unusual requirements for your wallpapers (like specific wallpapers at specific times or freshly generated images) there's no need to make it that complicated since XFCE has a built-in wallpaper changer. Just open the desktop settings, set the folder with your images and put a checkmark at the option to 'Change the background' and set the time.

Holger

I use my wallpaper as a weather monitor. The script first downloads a fresh satellite image, then sets it as the wallpaper. Depending on the time of day, it can pick either the natural colour image (1.6 &#956;m, 0.8 &#956;m, 0.6 &#956;m) or infrared (12.0 &#956;m, 10.8 &#956;m, 3.9 &#956;m).

---

