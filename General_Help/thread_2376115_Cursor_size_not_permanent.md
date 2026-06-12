---
title: "Cursor size not permanent"
date: 2017-10-30
forum: General Help
---

### Post by Cariboo1938 on 2017-10-30
I use ubuntu 16.04. 
I installed the tweak tool. 
From there I select Whiteglass and check mark "Use large cursors". 
After each restart the selected cursor comes up but in small size. 
How can I make it permanent large size?

---

### Post by RobGoss on 2017-10-30
Hello, you can download one of the cursor themes from the Gnome website and simply install it 

Gnome look
[https://www.gnome-look.org/browse/cat/107/ord/latest/](https://www.gnome-look.org/browse/cat/107/ord/latest/) 

You will need to download the themes, extract it then copy the content and paste it into the cursor theme folder

Then choose the cursor theme from the **tweak tool** and you should be good to go. They also have large ones as well

---

### Post by Cariboo1938 on 2017-10-30
Thanks for the hint...
As I am quite happy with the Whiteglass cursor I do not want to download others...
I only want the "Use large cursors" preference, which I choose with tweak, tool not to be changed on every reboot.

---

### Post by RobGoss on 2017-10-31
> **Cariboo1938 said:**
> Thanks for the hint...
As I am quite happy with the Whiteglass cursor I do not want to download others...
I only want the "Use large cursors" preference, which I choose with tweak, tool not to be changed on every reboot.

 Then you might want to see this post it might be of help [https://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](https://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

---

### Post by Cariboo1938 on 2017-10-31
I checked it and I was not able to find an answer there.
This are the cursors installed.
> jg@jg-MS-7596:~$ find /usr/share/icons ~/.icons -type d -name "cursors"
/usr/share/icons/DMZ-White/cursors
/usr/share/icons/redglass/cursors
/usr/share/icons/whiteglass/cursors
/usr/share/icons/DMZ-Black/cursors
/usr/share/icons/handhelds/cursors

 Is it a "Unity Tweak Tool" issue that the Preference "Use large cursors" gets unchecked/reset after each reboot?

---

### Post by vanadium on 2017-11-01
I am working with a command to increase the cursor size:
```

sh -c "sleep 6 && dconf write /org/gnome/desktop/interface/cursor-size 36"

```
You can put this in your autostart programs to have it set each time you log in (the setting does not stick).

---

### Post by Cariboo1938 on 2017-11-01
Thanks vanadium...
yes, this works well...
although there must be a size limit at size 36, right?

I think it is a work-around of a flaw in the Unity Tweak Tool, isn't it?

---

