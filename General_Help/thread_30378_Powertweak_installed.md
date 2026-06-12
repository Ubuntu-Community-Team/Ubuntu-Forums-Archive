---
title: "Powertweak installed"
date: 2005-04-28
forum: General Help
---

### Post by desheikh on 2005-04-28
Hi,

I installed powertweak but now I have know idea what the command to run it is  :-? 
Any one knows?... 
And btw is there some software which can list all the applications i have installed in gnome and allow me to run them?

Ali.

---

### Post by rutty on 2005-05-09
I had the same problem (the instructions are well hidden) but all you have to type are:

sudo gpowertweak

I'm not entirely sure how much you can change, or if you;d even want to, but that certainly launches the GUI after installed it. :)

---

### Post by SkyNet2029 on 2006-06-05
You can use the Debian Menu to display and Run ALL of your installed applications in both Ubuntu and Kubuntu. Easiest way is via an apt-get.

```
#apt-get update
#apt-get install menu
```

*Use the 'sudo' if not ran from an root terminal/Konsole.
* The update portion is optional, just a habit I have to ensure your apt-get is using the latest info,the repositories aren't 'dead' at the moment, etc. and to verify (I use the buggy mad-wifi from restricted modules) my connection is still alive ;-)

The Debian Menu neatly organizes into sub-directories all of your installed pkgs too, for a cleaner UI.
I realize it has been over a year since your inquiry, but i'm hoping my solution will help others if you already figured it out on your on.

---

