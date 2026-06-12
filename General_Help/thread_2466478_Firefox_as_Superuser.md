---
title: "Firefox as Superuser"
date: 2021-08-28
forum: General Help
---

### Post by Quarkrad on 2021-08-28
Running Mate 20.04  Firefox 91.0.2   everything is up-to-date.   When I launch ff the heading says Mozilla Firefox (as superuser) - tried this on a number on clean install virtual machines and every time ff seems to be running as the superuser.  I have also **sudo chown -R dad:dad ~/.mozilla**  One effect is when I backup my bookmarks e.g abcd.json I cannot find that file in either where I attempted to save it to (I've tried Home, Downloads, Desktop, .........) or anywhere searching in Filesystem.   I then opened caja as root via **sudo -H caja** and searched for the file again (looking in Filesystem). The file was found in /proc/7850/cwd.  I've just read a little about this folder but it is not right that when I save my bookmarks to say, my Downloads folder, it lands up in /proc/7850/cwd.   As far as I can tell ff is owned by dad although it says (as superuser) in the gui.

---

### Post by mikewhatever on 2021-08-28
You may want to provide the full path to the <.mozilla> folder:
> /home/dad/.mozilla
Another thing to check is the link at /usr/bin/firefox
> 
ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 25 Aug 23 19:55 /usr/bin/firefox -> ../lib/firefox/firefox.sh


What you have is not the default behavior, and looks very odd indeed.

---

### Post by grahammechanical on 2021-08-28
Who is the superuser (sudo) on that machine? Is it you? Have you considered that another family member has knowledge of your password and has used it to make changes to the system?

Check what permissions the other users have on that system and whether they have those permissions with your consent.

Regards

---

### Post by Impavidus on 2021-08-29
Does Firefox actually run as root or is the heading off? Check with ps or top.

How do you start Firefox? From command line or some launcher? Try both. If you use some launcher, there must be an associated .desktop file. Check that. Also look at the permissions of the executable file.```
ls -l /usr/bin/firefox /usr/lib/firefox/firefox.sh /usr/lib/firefox/firefox
```
Obviously, running Firefox as root not only messes up ownership of your Firefox profile, but is also a huge security risk.

---

### Post by Quarkrad on 2021-08-29
I am the sole (home) user of this machine - **dad**  so there are not any issues re a 3rd party.

```
dad@dadubuntu:~$ ls -l /usr/bin/firefox /usr/lib/firefox/firefox.sh /usr/lib/firefox/firefox
lrwxrwxrwx 1 root root     25 Aug 23 17:55 /usr/bin/firefox -> ../lib/firefox/firefox.sh
-rwxr-xr-x 1 root root 736648 Aug 23 17:55 /usr/lib/firefox/firefox
-rwxr-xr-x 1 root root   2667 Aug 23 17:55 /usr/lib/firefox/firefox.sh
dad@dadubuntu:~$ 

```

I cannot attach any attachments as I am not able to 'see' them. I will go onto my wife's machine to attach some pics

---

### Post by &amp;KyT$0P# on 2021-08-29
Are you using firejail or similar sandboxing software to run Firefox?

---

### Post by Quarkrad on 2021-08-30
Apologies for the delay responding and thanks for _all _your replies.  It appears the culprit was firejail - in hindsight I should have mentioned this in my first post but I never associated.  I have purged firejail and rebooted and all my issues seem to have disappeared - even adding an attachment to this post that I couldn't do yesterday.  However, firefox still tells me it is running as Superuser (see superuser.png) - I launch ff via the icon where the command is firefox %u   I also attached zwz1.jpg which shows the view I had when trying to attach a file to this post when firejail was installed.  If I reinstall firejail  (which I would prefer) is there a specific location I should use so I can add attachments?

---

### Post by Impavidus on 2021-08-30
Your first screenshot doesn't tell you're running Firefox as superuser. It tells you're viewing a webpage with the title "[ubuntu_mate] Firefox as Superuser", a title you created yourself by starting this thread. It looks the same on my box.

I'm sorry if that's too obvious.

---

### Post by &amp;KyT$0P# on 2021-08-30
It is a known issue with MATE's default window manager.  See [firejail documentation on this]("https://github.com/netblue30/firejail/wiki/Frequently-Asked-Questions#ive-noticed-the-title-bar-in-firefox-shows-as-superuser-is-this-normal").

> **Quarkrad said:**
> If I reinstall firejail  (which I would prefer) is there a specific location I should use so I can add attachments?

That is decided by your firejail profile for Firefox.  Do you have a custom one in [FONT=Courier New]~/.config/firejail/[/FONT] ?

---

### Post by Quarkrad on 2021-09-01
I haven't got ~/.config/firejail or how to edit a custom profile - just the standard profile set in /etc.  I played a little with firejail when it first came out but for some reason stopped using.  I'm going to refresh my understanding and get my head around the custom set ups and profiles. Thank you for you help.

---

