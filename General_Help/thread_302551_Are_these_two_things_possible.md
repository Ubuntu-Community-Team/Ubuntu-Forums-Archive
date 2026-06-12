---
title: "Are these two things possible?"
date: 2006-11-18
forum: General Help
---

### Post by Hydrargyri on 2006-11-18
Hello! I have been using Ubuntu for quite some time now, and am really enjoying it and getting the hang of it.

However, as I have an undying love of getting ahead of myself, I want to know if these two things are possible.

The first is that I recently got a fancy new SATA hard-drive and put 6.10 on it. Before that, and now, I have a PATA hard-drive partitioned in two - one for Windows, one for Ubuntu 6.06. Now, what I would like to do is get rid of the 6.06 partition and *expand* the Windows partition to fill the rest of the drive. I know that this is possible with a complete re-format, but is there a way to do this without reformatting Windows?

The second is that I have a few terminal-based programs that I need to use at school, but my computer (being a tower and not a laptop) is quite thoroughly immobile. Is there a way to set up my computer so that I can log on in terminal mode using SSH or putty or something? I have read a few threads on the general subject here, but they all seemed a bit too technical for me, or specific questions from someone already half-way there. Oh, and my computer is hooked up to an encrypted wireless router - does that change anything?

Thank you for reading! :)

---

### Post by Choad on 2006-11-18
maybe, and maybe

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) says yes but NTFS is always a bit shakey imo. as always when mesing with partitions, back up important stuff

and to the second question, if the school computers have some kind of ssh client, im sure there is no problem in setting up ssh. i dont know how to do it tho!

you could even set up a full remote desktop if the school would allow u to put on the client software

---

### Post by CatKiller on 2006-11-19
> **Hydrargyri said:**
> The first is that I recently got a fancy new SATA hard-drive and put 6.10 on it. Before that, and now, I have a PATA hard-drive partitioned in two - one for Windows, one for Ubuntu 6.06. Now, what I would like to do is get rid of the 6.06 partition and *expand* the Windows partition to fill the rest of the drive. I know that this is possible with a complete re-format, but is there a way to do this without reformatting Windows?

Yes, probably. I'd advise the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") since it will have the latest version on, but you should be able to use the Ubuntu live cd to do it. You'll want to issue a **sudo swapoff -a** if you use the Ubuntu disc, since that will mount your swap partition automatically, which makes deleting your swap partition difficult :)

You'll also need to restore the Master Boot Record for Windows, since you probably won't want GRUB there anymore. You do this using the Windows install cd. There are instructions on this forum, but it boils down to either **fdisk /mbr** or **fixmbr** depending on the version of Windows.

> The second is that I have a few terminal-based programs that I need to use at school, but my computer (being a tower and not a laptop) is quite thoroughly immobile. Is there a way to set up my computer so that I can log on in terminal mode using SSH or putty or something? I have read a few threads on the general subject here, but they all seemed a bit too technical for me, or specific questions from someone already half-way there. Oh, and my computer is hooked up to an encrypted wireless router - does that change anything?

The general steps you'll need to take are

Install the SSH server on your computer

Forward port 22 (I think) on your router to the computer you wish to connect to.

Use ssh user@host to connect from a school computer.

If your home computer has a dynamic IP address, you may have trouble finding it on the Internet. You could use Dynamic DNS to have a fixed name for a variable IP address. I don't know how it works, though.

Hopefully you'll be able to find enough information on each of the steps individually to be able to do the whole process yourself. Good luck!

---

### Post by Atomic Dog on 2006-11-19
Hirens boot disc?  Has everything you will ever need.

---

### Post by Hydrargyri on 2006-12-03
Hello!

First, thank you very much for helping me with SSH. It is working perfectly! However, naturally, I want to go one step further.

I was thinking of building a new computer, and as I was writing up the price chart and everything, I couldn't help but notice that +$150 monitor that was inevitably tacked on.

Seeing that everything I want to do on my linux box is through SSH, and I have that set up (thanks again!), do I need a monitor output at all for this computer? Would there be any instance when I would need a monitor on hand?

Along those lines, I had heard that SSH was rather dangerous - people have computers that do nothing but scan ports to password-guess SSH stuff, I've been told. To counter that, I created an admin-privelage-less account, and set the SSH server to only allow that account to log in. However, if it is possible to go monitor-less on my linux computer, I would not be able to do anything that required admin powers. I have a pretty good admin password, and I have a different port set up, and its not like I've posted my IP anywhere public. How realistic would the danger be if I opened up my admin account?

Thanks,
Hydrargyri

---

### Post by Jose Catre-Vandis on 2006-12-03
Do you need a monitor?

This depends on the resilience of your PC, how it can cope with power cuts, reboots, that kind of thing. If you can "take" a monitor to the box when you need to, and this is the monitor X is configured for, then dealing with "issues", rebuilds etc should be no problem. Running headless is made more simple if you only ever use the command line interface.

I have had a headless server running for @ four months, which I access through ssh and vnc remotely. I have only had to attach a monitor twice in all that time. HTH.

---

### Post by RAOF on 2006-12-03
> **Hydrargyri said:**
> ...
I was thinking of building a new computer, and as I was writing up the price chart and everything, I couldn't help but notice that +$150 monitor that was inevitably tacked on.

Seeing that everything I want to do on my linux box is through SSH, and I have that set up (thanks again!), do I need a monitor output at all for this computer? Would there be any instance when I would need a monitor on hand?

Along those lines, I had heard that SSH was rather dangerous - people have computers that do nothing but scan ports to password-guess SSH stuff, I've been told. To counter that, I created an admin-privelage-less account, and set the SSH server to only allow that account to log in. However, if it is possible to go monitor-less on my linux computer, I would not be able to do anything that required admin powers. I have a pretty good admin password, and I have a different port set up, and its not like I've posted my IP anywhere public. How realistic would the danger be if I opened up my admin account?
...

You can forward X connections through SSH (it's the option "X11Forwarding yes" in /etc/ssh/sshd_config - I think it's on by default).  Basically, that means that you can ssh in to the box and run **firefox** or whatever and it'll be run on the remote box and displayed on your local box.

You can also do a complete remote login (just like a local login) from GDM (from the "options" menu on the bottom left, by default).  I've never set that up, though.

If you're concerned about security, you can make your ssh virtually impregnable by using RSA or DSA keys.

You want to have this in your /etc/ssh/sshd_config
```
# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no
                                                                                
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no
                                                                                
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

```

This will **disable** logins without using the keys.  You will also need to generate the SSH keys by running **ssh-keygen** (generally on the system you want to connect **from**).  This will create (by default) two files - ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub.  The **id_rsa** file is your **private key** - this is what you'll need to login with.  The **id_rsa.pub** file is the public key associated with the private key.  You add the contents of this file to the ~/.ssh/authorized_keys on whatever system (and whatever user) you want to be able to login to.

Now you will be unable to login to that system except with the private key.  People just guessing usernames/passwords on your ssh port will always and automatically fail.  Basically the only way ssh would now prove to be a security vulnerability would be an exploit in the ssh server itself.

You might want to check out the man page for ssh-keygen ("man ssh-keygen").  There are a bunch of options, but the particularly useful one is requiring a passphrase to unlock the private key.  So, even if someone gets a hold of your key, there's still at least as good security as you have now.

---

