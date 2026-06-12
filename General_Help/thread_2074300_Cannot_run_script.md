---
title: "Cannot run script"
date: 2012-10-21
forum: General Help
---

### Post by RFXCasey on 2012-10-21
Hey all, trying to install and run a ts3 server on Ubuntu server 64bit. I've downloaded that correct package and unzipped it. I am trying to the ts2server_startscript.sh to run but it will not. I've tried chmod a+x on the script but still won't launch and says command not found. Help this is driving me nutz.

---

### Post by RFXCasey on 2012-10-21
Anyone?

---

### Post by Lars Noodén on 2012-10-21
Are you including the path when you try to run the script?  If you are in the same directory as the script, the following might work:

```

 ./ts2server_startscript.sh

```

By the way, have you made sure that the package is not already in the repositories before trying to install manually?  Using the repositories will be less work for maintaining the software.

---

### Post by RFXCasey on 2012-10-27
> **Lars Noodén said:**
> Are you including the path when you try to run the script?  If you are in the same directory as the script, the following might work:

```

 ./ts2server_startscript.sh

```

By the way, have you made sure that the package is not already in the repositories before trying to install manually?  Using the repositories will be less work for maintaining the software.

yep worked like a charm, but I don't understand why I need to do "./" I don't think the script is hidden.

Also, I don't log in as root. Is it ok to run a server under my regular user name or should I create a another user for it and run it under that one? Read a post that suggested doing this for security reasons. If I was also going to run a site/forum on the same server should I create an additional user for that as well so that the TS3 and site servers are running under different user accounts?

---

### Post by claracc on 2012-10-27
Here, the . doesn't mean a hidden file but where actually is the address to find the script. So, ./ is addressing the home user directory where the .sh script is.

---

### Post by RFXCasey on 2012-10-27
> **claracc said:**
> Here, the . doesn't mean a hidden file but where actually is the address to find the script. So, ./ is addressing the home user directory where the .sh script is.

I see, I was in the directory where the script was I believe when I tried to start is without the ./, why is it still needed if you are in the current directory?

---

### Post by claracc on 2012-10-27
Because you have to indicate where is the .sh: ./ means from here (where you are), executes the .sh. This is the way running script work.

---

### Post by Lars Noodén on 2012-10-27
> **RFXCasey said:**
> I see, I was in the directory where the script was I believe when I tried to start is without the ./, why is it still needed if you are in the current directory?

If you type 'echo $PATH', you can see all the directories that get searched for programs.  For good reason '.', the current directory, is not among them.  So to run a program that is in your current directory you have to specify the path explicitly.  If you know the full path you can specify that, too: /home/rfxcasey/bin/ts2server_startscript.sh

If you don't want to specify the path each time you run it, move it to ~/bin/ or /usr/local/bin/

---

### Post by Abhinav Kumar on 2012-10-27
a small point - chmod was only changing permissions for the script file to make it executable.
./ actually executes it

---

