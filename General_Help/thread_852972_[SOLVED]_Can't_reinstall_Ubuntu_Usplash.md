---
title: "[SOLVED] Can't reinstall Ubuntu Usplash"
date: 2008-07-08
forum: General Help
---

### Post by Spaceman9 on 2008-07-08
I was running YouTube and Audacity and Audacity messed up and I had to push the warm reboot button. Now when I boot up and shut down I don't see the Ubuntu logo and progress bar. Instead there's only text before the login screen and only text at shut down.

I tried everything on this page [https://help.ubuntu.com/community/USplash?action=fullsearch&context=180&value=ubuntu+bootup+logo&titlesearch=Titles](https://help.ubuntu.com/community/USplash?action=fullsearch&context=180&value=ubuntu+bootup+logo&titlesearch=Titles) but it didn't bring back the Ubuntu logo and progress bar.

I typed sudo usplash into a terminal and that put the Ubuntu logo on the screen for a few seconds so it's still installed on my hard drive. I just can't get it to run at boot up and shut down.

So what do I have to do to make it run again at boot up and shut down? Thankx for any help.

---

### Post by Spaceman9 on 2008-07-08
Can anyone help me with this problem??

---

### Post by sayakb on 2008-07-08
Install Startupmanager:
```
sudo apt-get install startupmanager
```
Launch it from [B]System->Administration->StartUp-Manager
[/B]Click on **Appearance** tab and select Usplash-theme-ubuntu at the drop menu at the bottom. If it fails to work, you may download other usplash themes from gnome-look.org and install it using Startup Manager and see if they work.

---

### Post by Spaceman9 on 2008-07-08
Thank you very much LinuxIsInnovation. I already had StartUp-Manager installed and last night I checked that it was set to ubuntu-usplash on the screen and it was but I never though of changing that. Just now I changed it to ubuntu-studio and rebooted. It didn't put ubuntu-studio on the screen. So I used StartUp-Manager to change it back to ubuntu-usplash and rebooted and there it was, just like before at bootup. It's fixed!!!!

The only other problem is that now when it goes into the desktop it runs Nautilus. How do I fix that??

---

### Post by sayakb on 2008-07-08
At a terminal:
```
rm ~/.gnome2/session
```
Should do it. Make sure you have "Auto remember running apps" disabled in System->Preferences->Sessions->Session Options

---

### Post by Spaceman9 on 2008-07-08
Ok, I looked for .gnome/session and found it


[Default]
0,id=117f000101000121549876100000061800000
0,RestartStyleHint=2
0,Priority=40
0,Program=gnome-panel
0,CurrentDirectory=/home/bruce
0,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-Vlys7U/ 
0,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-Vlys7U/ --sm-client-id 117f000101000121549876100000061800000 --screen 0 
1,id=117f000101000121549876200000061800002
1,RestartStyleHint=2
1,Priority=20
1,Program=metacity
1,CurrentDirectory=/home/bruce
1,DiscardCommand=rm -f /home/bruce/.metacity/sessions/117f000101000121549876200000061800002.ms 
1,CloneCommand=metacity 
1,RestartCommand=metacity --sm-client-id 117f000101000121549876200000061800002 
2,id=117f000101000121549876200000061800001
2,RestartStyleHint=2
2,Priority=40
2,Program=nautilus
2,CurrentDirectory=/home/bruce
2,CloneCommand=nautilus --sm-config-prefix /nautilus-Zc11uX/ 
2,RestartCommand=nautilus --sm-config-prefix /nautilus-Zc11uX/ --sm-client-id 117f000101000121549876200000061800001 --screen 0 
3,id=117f000101000121549876400000061800003
3,RestartStyleHint=1
3,Program=update-notifier

In there you can see the commands to start Nautilus. Instead of typing what you wrote at the command line could I instead edit the session file?

I know I should save the session file as sessionold first. I read another thread where it said if the session file is deleted it will be replaced automatically at the next bootup. I think I need to buy a book about Ubuntu. Otherwise I can see myself having to ask questions in the forum for the rest of my life.

---

### Post by Spaceman9 on 2008-07-08
I used rm ~/.gnome2/session to solve the problem. After rebooting, everything for the desktop came back the way it should be. Thankx very much for your help.

---

