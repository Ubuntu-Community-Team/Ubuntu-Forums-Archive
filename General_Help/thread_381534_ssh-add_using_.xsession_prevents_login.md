---
title: "ssh-add using .xsession prevents login"
date: 2007-03-11
forum: General Help
---

### Post by waldschm on 2007-03-11
I'm currently running Edgy on my laptop and generated a keypair to use with ssh. What I tried to do next was to ssh-add the key to ssh-agent during startup by adding the following command to my .xsession file in my home directory.

```

ssh-add /home/myusername/.ssh/id_rsa

```

and then set this file to be executable with chmod +x. The idea is to have a dialog box pop up on startup to unlock my key and add it to the agent. What happens however is the session crashes right away and gives the following error:

```

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

(View details ~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...
Identity added: /home/myusername/.ssh/id_rsa (/home/myusername/.ssh/id_rsa)

```

So my question is, am I going about this incorrectly? Is there another place from which I should be invoking the ssh-add command or another way to add my key to ssh-agent during startup?

Thanks for any help you can provide.

---

### Post by max.spicer on 2007-05-25
I think that you've effectively tried to set your window manager to be ssh-add instead of Gnome.  ssh-add exits as soon as you enter your password, hence the less than 10 seconds message.  There's probably a custom Gnome startup script that you could use instead, but what I've done is simply added an ssh-add session in Gnome:

System->Preferences->Sessions->New - Enter ssh-add under Name and Command.

I use gstm, and needed to make sure that ssh-add ran before gstm, otherwise I got two prompts for my key password.  I've solved this by creating a session that launches both, as follows:

sh -c 'ssh-add && gstm'

Max

> **waldschm said:**
> I'm currently running Edgy on my laptop and generated a keypair to use with ssh. What I tried to do next was to ssh-add the key to ssh-agent during startup by adding the following command to my .xsession file in my home directory.

```

ssh-add /home/myusername/.ssh/id_rsa

```

and then set this file to be executable with chmod +x. The idea is to have a dialog box pop up on startup to unlock my key and add it to the agent. What happens however is the session crashes right away and gives the following error:

```

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

(View details ~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:0.Xservers" -h "" -l ":0" "myusername"
/etc/gdm/Xsession: Beginning session setup...
Identity added: /home/myusername/.ssh/id_rsa (/home/myusername/.ssh/id_rsa)

```

So my question is, am I going about this incorrectly? Is there another place from which I should be invoking the ssh-add command or another way to add my key to ssh-agent during startup?

Thanks for any help you can provide.

---

