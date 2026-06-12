---
title: "Bash And Yum"
date: 2012-12-02
forum: General Help
---

### Post by UltimateCat on 2012-12-02
Hi!:KS:

I have been reading and studying Bash for weeks and it still eludes me to some degree.  I didn't look at the Advanced Bash Guide because I haven't been able to make it past my first script. Here's where I have been learning from:
[http://www.tldp.org/](http://www.tldp.org/)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

My first script:
```
#!/bin/bash
#my first script
echo "Hello World!"

```

What I don't understand is where do I type 'chmod 755 my_script'?
And where would I put ./my_script and echo $PATH
Also; if I tell the terminal to make a directory 'mkdir bin'
Where will that new directory be?

I read that a better way would be for me to edit my .bash_profile to include the command but I don't understand what this practice even means-
Please explain in some other way so I can know how to perform the right things for the terminal to work this simple script for me.

And than there is Yum which I have been reading about for days trying to understand how it works with Fedora.

Is YUM a utility like apt?

Any answers would be greatly appreciated as I'm trying to learn.
Thanks in advance

---

### Post by Vaphell on 2012-12-02
> What I don't understand is where do I type 'chmod 755 my_script'?

in terminal because it's a one time operation. Alternatively you can use **+x** instead of 755 which is more human readable and doesn't touch r,w permissions at all.
```
chmod +x file
```

> And where would I put ./my_script and echo $PATH
Also; if I tell the terminal to make a directory 'mkdir bin'
Where will that new directory be?

I read that a better way would be for me to edit my .bash_profile to include the command but I don't understand what this practice even means-
Please explain in some other way so I can know how to perform the right things for the terminal to work this simple script for me.

depends what the script is supposed to do.
.bashrc and .bash_profile are scripts that initialize bash environment when you open it.
[http://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment](http://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment)

you can run script and echo $PATH in both terminal and in scripts. They are just commands and there is not much difference between running them in interactive mode in terminal or in an automated collection of commands (script). 

*mkdir bin* is executed in context of current location (directory is given a relative path, not absolute /dir/dir/dir), which means that unless you used *cd* to change current dir, bin will be created under your $HOME. If you are unsure what is your current location, run *pwd* or *echo $PWD*, though your prompt should show current dir already

> And than there is Yum which I have been reading about for days trying to understand how it works with Fedora.
Is YUM a utility like apt?


yes

---

### Post by UltimateCat on 2012-12-03
Thanks for the confirmation that Yum is a utility.

So; since Yum is a utility do I really need to install RPM?

Didn't realize it was so late!  Be back tomorrow-:)

---

### Post by drmrgd on 2012-12-03
No, Yum is a package manager for Fedora (and other RPM based systems), while Apt is the package manager for Ubuntu (and other Debian base systems).  You can (and should) stick with Apt and can probably use it in the place of Yum when called for.

---

### Post by UltimateCat on 2012-12-06
So after I install Fedora(laptop) I should use Yum and not Apt?

Asking because I need clarification as I don't have much help at home.

---

### Post by UltimateCat on 2012-12-06
> **Vaphell said:**
> in terminal because it's a one time operation. Alternatively you can use **+x** instead of 755 which is more human readable and doesn't touch r,w permissions at all.
```
chmod +x file
```

depends what the script is supposed to do.
.bashrc and .bash_profile are scripts that initialize bash environment when you open it.
[http://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment](http://stackoverflow.com/questions/415403/whats-the-difference-between-bashrc-bash-profile-and-environment)

you can run script and echo $PATH in both terminal and in scripts. They are just commands and there is not much difference between running them in interactive mode in terminal or in an automated collection of commands (script). 

*mkdir bin* is executed in context of current location (directory is given a relative path, not absolute /dir/dir/dir), which means that unless you used *cd* to change current dir, bin will be created under your $HOME. If you are unsure what is your current location, run *pwd* or *echo $PWD*, though your prompt should show current dir already



yes

Not sure why my first script and understanding Bash has been so hard for me but I'm not going to give up.

Thanks for the link to the article at stack overflow-

I'll look in my Debian Administrators Book and see if there is a chapter about Bash that I can read to learn more. This is what I have so far:

#!bin/bash
#my first script
echo "Hello World!"
echo $PATH

Don't have a clue what to write after the $PATH in the 4th line.
I'd like to write a script for 2 cron jobs to run but not sure what the approiate arguments would be written.
I'm guessing something like:
<run rkhunter and chkrootkit && initial >> at 8 O'clock p.m. every Friday>?

---

### Post by Sef on 2012-12-06
> So after I install Fedora(laptop) I should use Yum and not Apt?

Yes. You should use the type of package manager that your distro comes with.

---

### Post by UltimateCat on 2012-12-06
> **Sef said:**
> Yes. You should use the type of package manager that your distro comes with.
Thanks for the confirmation.

---

