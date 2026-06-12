---
title: "ssh aliases"
date: 2007-12-13
forum: General Help
---

### Post by Mateo on 2007-12-13
Ok, so my goals is simple.  I want to type 'ssh desktop' instead of having to type 'ssh matthew@192.168.1.104' to ssh into my desktop computer.  This seemingly simple task is really not as simple as I'd hoped.  If you have a suggestion, I'd like to hear it, but I have some requirements for how I want this done (please do not make a suggestion that doesn't fit the requirements.

Requirements:

1)  I log-in by typing:  ssh desktop
2) Has to log-in to the specific user (in this case 'matthew').
3) Will work on all shells (sh, bash, zsh, etc.) even those i might not currently have installed.

Optional (but i'd really like it)

1) It would be great if this would work under all users, current and future.

thanks!

---

### Post by chippy99 on 2007-12-13
Does [http://marc.info/?l=openssh-unix-dev&m=110267748024284&w=2](http://marc.info/?l=openssh-unix-dev&m=110267748024284&w=2) do what you want ?

---

### Post by p_quarles on 2007-12-13
I guess I'm not seeing what wouldn't be simple about this, because you didn't say anything about what you've already tried. The only thing I can see that won't work is using an unescaped space character inside an alias. If you changed it to something like "ssh-desktop" (exactly the form I use, as it happens), it'll work fine. 

Anyway, I know of no way to make an alias that will automatically be added to all possible shell environments, since each one will have its own list of aliases. The thing to do there would be to write a short script. A script will work in any shell, since it will itself specify what environment it runs in. 

As far as making such a script compatible with any user, you should be able to use a regular expression or xargs to grab the output of the 'whoami' command, and insert that into the ssh arguments. I'm not enough of a scripting wiz to tell you how, but that's where you'd want to look.

---

### Post by Mateo on 2007-12-13
> **p_quarles said:**
> I guess I'm not seeing what wouldn't be simple about this, because you didn't say anything about what you've already tried. The only thing I can see that won't work is using an unescaped space character inside an alias. If you changed it to something like "ssh-desktop" (exactly the form I use, as it happens), it'll work fine.

Violates requirement #1.

> Anyway, I know of no way to make an alias that will automatically be added to all possible shell environments, since each one will have its own list of aliases.

Maybe I shouldn't say "alias" since that is confusing.  I don't mean a shell alias in the sense of .bash_aliases and such.  Though I would do it that way if it can be done without all of my requirements.  I agree that it doesn't seem likely that you can do this with all shells though.

> The thing to do there would be to write a short script. A script will work in any shell, since it will itself specify what environment it runs in.

Violates requirement #1.

---

### Post by Mateo on 2007-12-13
> **chippy99 said:**
> Does [http://marc.info/?l=openssh-unix-dev&m=110267748024284&w=2](http://marc.info/?l=openssh-unix-dev&m=110267748024284&w=2) do what you want ?

Maybe.. i'm going to look into this.

---

### Post by Mateo on 2007-12-13
Ok, so I think I do it like this:  ~/.ssh/config

host 192.168.1.104
        Hostname desktop
        User matthew


Is this correct?

Is there a system-wide file for this?

---

### Post by p_quarles on 2007-12-13
> **Mateo said:**
> Violates requirement #1.



Maybe I shouldn't say "alias" since that is confusing.  I don't mean a shell alias in the sense of .bash_aliases and such.  Though I would do it that way if it can be done without all of my requirements.  I agree that it doesn't seem likely that you can do this with all shells though.



Violates requirement #1.
Well, maybe you misunderstood: my response was a polite way of saying that requirement #1 would require renaming the ssh client, aliasing it, and essentially rewriting the coreutils. 

Anyway, chippy99's suggestion will also work, but will also violate "requirement #1" since you'll need a separate hostname for each user.

---

### Post by Mateo on 2007-12-13
> **p_quarles said:**
> Well, maybe you misunderstood: my response was a polite way of saying that requirement #1 would require renaming the ssh client, aliasing it, and essentially rewriting the coreutils. 

Anyway, chippy99's suggestion will also work, but will also violate "requirement #1" since you'll need a separate hostname for each user.

There's only 1 user on the ssh server computer that i'm logging into.

---

### Post by p_quarles on 2007-12-13
> **Mateo said:**
> There's only 1 user on the ssh server computer that i'm logging into.

> **Mateo said:**
> Optional (but i'd really like it)

1) It would be great if this would work under all users, current and future.

thanks!
. . .

---

### Post by Mateo on 2007-12-13
maybe i'm misunderstanding how ssh_config works, but I thought the User field denotes the user that you log into on the ssh server computer, no?

---

### Post by chippy99 on 2007-12-13
/etc/ssh/ssh_config should define it system wide, have a look at the man page for ssh_config

---

### Post by Thanoulis on 2007-12-13
I do not know if ssh understand alliases/shortcuts, but you can write a shell script to do the job.
Something like:
```
#!/bin/bash
ssh <whatever>@<wherever>
```

---

### Post by MrFSL on 2007-12-13
Sounds like you are making this extremely difficult for little reason.

The IP addresses can be converted to hostnames using your computer's host file:
```
sudo gedit  /etc/hosts
```

Next, if you can't find a global way to organize your ssh profiles, why not just script it out and through your small and simple scripts in your path?

---

### Post by Mateo on 2007-12-13
> **Thanoulis said:**
> I do not know if ssh understand alliases/shortcuts, but you can write a shell script to do the job.
Something like:
```
#!/bin/bash
ssh <whatever>@<wherever>
```

Violates requirement #1.

---

### Post by Mateo on 2007-12-13
> **MrFSL said:**
> Sounds like you are making this extremely difficult for little reason.

The IP addresses can be converted to hostnames using your computer's host file:
```
sudo gedit  /etc/hosts
```

Next, if you can't find a global way to organize your ssh profiles, why not just script it out and through your small and simple scripts in your path?

It is my understanding is that /etc/hosts doesn't deal with users, so this method is out.

---

### Post by Mateo on 2007-12-13
I editted /etc/ssh/ssh_config  and added this:

Host 192.168.1.104
    Hostname desktop
    User matthew


But that doesn't work.  I type:  ssh desktop   and it says name or service not known.

---

### Post by p_quarles on 2007-12-13
I think I've got the answer. Add the following to the .bashrc file in your home folder:
```
alias ssh desktop='opensesame'
```
I don't mean to be rude, but what you're asking for requires a workaround. You're not going to get a solution that meets all of your requirements without rewriting code and/or adding innovative regular expressions to your /etc/ssh/ssh_config file.

---

### Post by Mateo on 2007-12-13
Nope, got it working, had the Host switched around, should have been:

Host desktop
    Hostname 192.168.1.104
    User matthew

works perfectly, fits within all of my requirements.  Happy is me!

---

### Post by dagnabit dang doohickey on 2007-12-13
Create a ~/.ssh/config file if it doesn't already exist and edit it to include the following:
## My Desktop
Host desktop
HostName 192.168.1.104
User matthew

---

