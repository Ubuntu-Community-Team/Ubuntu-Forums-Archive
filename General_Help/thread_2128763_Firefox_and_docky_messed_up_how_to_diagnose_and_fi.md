---
title: "Firefox and docky messed up how to diagnose and fix"
date: 2013-03-24
forum: General Help
---

### Post by DrScum on 2013-03-24
I have a new lubuntu install (12.04) on a desktop system. 
Worked great until I had a power failure during installation of kaffeine. I was able to fix broken packages and finish the installation. However, docky and firefox, which worked perfectly before, are somehow messed up.

When I start the system I get an error message that some application crashed but didn't identify itsself. When I try to start firefox from the applications menu the same message occurs. When I try to start docky from the applications menu nothing happens. I did try to reinstall both applications firefox and docky using synaptic package manager  but it didn't help.

Other software can be started normally from the applications menu. 

How do I diagnose identify and fix this?

Help is appreciated.

---

### Post by ibjsb4 on 2013-03-24
Try starting them in terminal and see what errors you get.

---

### Post by DrScum on 2013-03-24
when starting firefox from terminal I get:
"while connecting to sesson manager: Authentication rejected, rason: None of the authentication protocols specified are supported and host based authentication failed"

when staring docky from terminal I get millions of lines of text, this one looks like an error message:

"fatal unhandled exception: System.xml.XmlExeption: document element did not appear file:///home/<username>/.local/share/docky/plugins/addin-db-001/config.xml Line 1 Pos 1"

---

### Post by ibjsb4 on 2013-03-24
You say that you tried reinstalling firefox, but I believe that keeps your configuration files intact.  So I suggest renaming your /home/user name/. mozilla folder and try firefox again.  Are you using SSH?

---

### Post by DrScum on 2013-03-24
Don't know exactly what SSH is, don't use it, at least not that I know of.

Renamed the .mozilla file in my home directory and AFTER THAT reinstalled firefox (after complete removal). When I try to start the program I get the message that the profile couldn't be loaded. 

Then I renamed back to .mozilla and got the same error as described in my second post.
Then I renamed the profiles.ini file in .mozilla/firefox when I start firefox then I am asked to create a profile, when I try to do that the process finishes with an error message implying that the directory is not writeable.

I am beginning to believe that the problems I am facing have something to do with user rights. Additional evidence in that direction is the fact that I can't use the shutdown procedure the way it used to be, when I try nothing happens. The only "legal" way out at the moment ist open a terminal and input "sudo halt". I will be going ahead, create a new user and see if the new user has the same problems. 

Any additional ideas are most welcome

---

### Post by DrScum on 2013-03-24
I went for crude action:

enabled root login, logged in as root. Applications worked fine (including firefox and docky) when logged in as root.

deleted my original user account and generated a new one.

Set the new account up the way it was before and was back to where I was about 24h ago.

---

