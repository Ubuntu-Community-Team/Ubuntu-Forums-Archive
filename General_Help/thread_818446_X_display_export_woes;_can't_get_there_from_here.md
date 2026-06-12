---
title: "X display export woes; can't get there from here"
date: 2008-06-04
forum: General Help
---

### Post by sfordin on 2008-06-04
I recently rebuilt my Ubuntu machine, installing Kubuntu 8.04 from scratch after previously running 7.10 through Gnome. I'm sure I'm just missing some simple fix, but I can't figure out what needs to be done. The problem is that I want to export the display of various Solaris X apps to my Linux box, but I'm getting unable to open display" errors or, with certain apps, "uncaught galaxy exception" errors.

What I've done in the past, and it's worked on every version of Linux I've ever used over the years, including 7.10, is the following:

1.   linuxbox$ xhost +<solarisbox>
2.   linuxbox$ xhost +localhost
3.   linuxbox$ ssh -X <solarisbox> -l <solaris_user_name>
4.   solarisbox$ setenv DISPLAY <linuxbox>:0.0
5.   solarisbox$ <run some app>

If I omit step 4 -- which I should be able to do because I invoked ssh with the -X option -- I can run some apps, like emacs and firefox, but some other apps, like Arbortext Editor, are stupid and throw "uncaught galaxy exception" errors. If I include step 4, every app throws the "unable to open display" error. So I'm in a bind: some apps seem to require that the DISPLAY variable be explicitly set, while others will only work if DISPLAY is not explicitly set. In any case, all of this, steps 1-5, used to work for all apps before I upgraded to Kubuntu 8.04. I'm confused.

Any suggestions? Thanks in advance,

Scott

---

### Post by sfordin on 2008-06-09
I found the answer in a thread titled [Run Grahics (X server) on Sun remotely from Ubuntu]("http://ubuntuforums.org/showthread.php?t=522702&highlight=setenv+DISPLAY"), with the answer coming from PaulFr. Thanks, PaulFr!

I'm running KDE on the Ubuntu side, so the short answer was to edit my /etc/kde3/kdm/kdmrc file, commenting out the  out the "ServerArgsLocal=-nolisten tcp" line in the [X-:*-Core] section, and then rebooting.

Hope this helps someone else.

---

