---
title: "What happens if you execute &quot;apt-get auto-remove .y&quot;"
date: 2018-04-14
forum: General Help
---

### Post by janidj on 2018-04-14
Hey Folks,


maybe I am the biggest idiot in the world (alternatively, I'm just a quick tipper ](*,)). Anyways, I accidentally executed the command


"apt-get auto-remove .y"


on my Ubuntu 16.04 server with the root user. Of cause, I know that you shouldn't use the root user for everything, but I did.
Shame on me :-({|=. 


So what now? Reinstall the Server? 


I have restarted it and anything seems to work fine. Does autoremove need "-y" to deinstall a given package? And before you 
ask I know that the command should be spelled out autoremove and not auto-remove, but this is what I typed.


Thanks in advance for any kind of help!


Greetings Jani

---

### Post by cariboo on 2018-04-14
Did you not see the following message?

```
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```

---

### Post by Bashing-om on 2018-04-14
janidj; Hello - Welcome to the foum .

> 
"apt-get auto-remove .y"

could not have done anything, as there is no such packages as ' auto-remove' and  '.y' for the package manager to "get" . Did you not see an advisory to that effect in the terminal ?

[INDENT][INDENT]nothing to sweat
[/INDENT][/INDENT]

---

### Post by janidj on 2018-04-14
Hey,


thanks for the quick answer!


> **cariboo said:**
> Did you not see the following message?


```
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

```


I did not type "yes" or "y" or anything that could potentially be understood as yes. But The console output was extremely long and weird. Especially if you use Putty without log activated ( :facepalm: ). I tried to reproduce the output with the "-s" parameter and I didn't know how accurate this is after I executed the command in the first place, but here is the output:


[https://pastebin.com/9BUQWuqz](https://pastebin.com/9BUQWuqz) (Part 1)
[https://pastebin.com/KEQppPhQ](https://pastebin.com/KEQppPhQ) (Part 2)


@Bashing-om
I would agree if the dry-run wouldn't give me any results


Jani

---

### Post by mc4man on 2018-04-14
> **Bashing-om said:**
> janidj; Hello - Welcome to the foum .


could not have done anything, as there is no such packages as ' auto-remove' and  '.y' for the package manager to "get" . Did you not see an advisory to that effect in the terminal ?

[INDENT][INDENT]nothing to sweat
[/INDENT][/INDENT]

auto-remove is an alias for autoremove. The .y however can cause some really unintended consequences 
(- you can try on your Desktop install with the -s  option to see how bad.

If there was a warning about essential packages to be removed it would not of waited for any confirmation.

---

### Post by janidj on 2018-04-14
@mc4man what du you think would be the best? I mean I rebooted the server and nothing seams to have problems (Kubernetes; Docker; other system internal things).

---

### Post by yetimon_64 on 2018-04-14
You could try and look in /var/log/apt/history.log and see what the system removed for that command, if it removed anything at all.

That command should only removed orphaned packages no longer needed by the system. But as others have said the "-y" option can make it dangerous to use at times (I have had it render my system useless in the past requiring a re-instal, largely because of my own carelessness at the time).

That history file exists on desktop installs, I am not sure if the server install has the same file but I would expect it to be on a server as well. May be worth a look to see if anything was removed by the command if it exists on your install.

Try the command ...
```
cat /var/log/apt/history.log | less
``` and use the page down or end keys to skip to the bottom of the file to see the last entries (if your install has the file, I am on 14.04 so not entirely sure about your set up).

---

### Post by janidj on 2018-04-15
Okay, fortunately, I got this log file. If I get it correct this file contains any package that I purged or installed, right? If so then thank god I did not remove anything :D.

@cariboo, @Bashing-om, @mc4man and  @yetimon_64 thank you all for your quick help. =d>

```

Start-Date: 2018-04-09  23:06:34
Commandline: apt-get install -y htop
Install: htop:amd64 (2.0.1-1ubuntu1)
End-Date: 2018-04-09  23:07:27


Start-Date: 2018-04-11  20:51:28
Commandline: apt-get install -y zsh
Install: zsh:amd64 (5.1.1-1ubuntu2.2), zsh-common:amd64 (5.1.1-1ubuntu2.2, automatic)
End-Date: 2018-04-11  20:51:40


Start-Date: 2018-04-11  20:55:58
Commandline: apt-get install fonts-powerline -y
Install: fontconfig-config:amd64 (2.11.94-0ubuntu1.1, automatic), fontconfig:amd64 (2.11.94-0ubuntu1.1, automatic), fonts-dejavu-core:amd64 (2.35-1, automatic), libfontconfig1:amd64 (2.11.94-0ubuntu1.1, automatic), fonts-powerline:amd64 (2.3-1ubuntu0)
End-Date: 2018-04-11  20:56:06


Start-Date: 2018-04-11  21:01:44
Commandline: apt-get purge -y zsh
Purge: zsh:amd64 (5.1.1-1ubuntu2.2)
End-Date: 2018-04-11  21:01:45


Start-Date: 2018-04-11  21:01:54
Commandline: apt-get purge -y fonts-powerline
Purge: fonts-powerline:amd64 (2.3-1ubuntu0)
End-Date: 2018-04-11  21:01:54


Start-Date: 2018-04-11  21:02:03
Commandline: apt-get autoremove
Remove: fontconfig-config:amd64 (2.11.94-0ubuntu1.1), fontconfig:amd64 (2.11.94-0ubuntu1.1), fonts-dejavu-core:amd64 (2.35-1), libfontconfig1:amd64 (2.11.94-0ubuntu1.1), zsh-common:amd64 (5.1.1-1ubuntu2.2)
End-Date: 2018-04-11  21:02:05


Start-Date: 2018-04-14  21:05:11
Commandline: apt-get purge -y nfs-kernel-server nfs-common
Purge: nfs-kernel-server:amd64 (1:1.2.8-9ubuntu12.1), nfs-common:amd64 (1:1.2.8-9ubuntu12.1)
End-Date: 2018-04-14  21:05:43


# I did this one on purpose after I accidental typed the wrong command.


Start-Date: 2018-04-14  21:09:57
Commandline: apt-get autoremove
Remove: libtirpc1:amd64 (0.2.5-1), libevent-2.0-5:amd64 (2.0.21-stable-2ubuntu0.16.04.1), keyutils:amd64 (1.5.9-8ubuntu1), rpcbind:amd64 (0.2.3-0.2), libnfsidmap2:amd64 (0.25-5)
End-Date: 2018-04-14  21:10:02



```

---

### Post by mc4man on 2018-04-15
Just to note:
The op  posted using  .y not -y
Here auto-remove -y removes 1 package
.y removes 1445 packages, little bit of a difference..

Maybe you meant -y not .y?

Edit: to see effects of .y on a Desktop install go 
```
sudo apt-get auto-remove -s .y
```
or because it'll exceed most terminal scroll backs, log in home folder.
```
sudo apt-get auto-remove -s .y >  1.log
```

I'm guessing .,  removed, see post 13

---

### Post by yetimon_64 on 2018-04-15
> **mc4man said:**
> Just to note:
The op  posted using  .y not -y
Here auto-remove -y removes 1 package
.y removes 1388 packages, little bit of a difference..

Maybe you meant -y not .y?

Edit: to see effects of .y go 
```
sudo apt-get auto-remove -s .y
```
or because it'll exceed most terminal scroll backs, log in home folder.
```
sudo apt-get auto-remove -s .y >  1.log
```

I'm guessing .y removes all automatically installed packages

Good pick, I had been misreading the .y as -y.
Seems on 14.04 the auto-remove alias does nothing but your simulation command with autoremove and ".y" sure is an eye opener. I think you may be guessing right by my running of that command. Cheers, yeti.

---

### Post by janidj on 2018-04-15
Yes, I typed ".y" not "-y", but the file @yetimon_64 mentioned didn't contain any removed packages through this command. So do I have to worry now? Or did I get away with a blue eye? Jani

---

### Post by mc4man on 2018-04-15
> **janidj said:**
> Yes, I typed ".y" not "-y", but the file @yetimon_64 mentioned didn't contain any removed packages through this command. So do I have to worry now? Or did I get away with a blue eye? Jani
I guess that comes down to does a server install or your server install have any packages marked as automatically installed. Based on what you've experienced maybe not? ( or none that important
The pastebin stuff  would be irrelevant as it was subsequent to the 1st. run of the command which would have removed all automatically installed packages, if any.
Your history.log doesn't show .y
So I'd guess you're ok..

On a Desktop install that command would pretty much destroy the install in a matter of seconds, the effect would be obvious on reboot or attempted reboot..

---

### Post by rsteinmetz70112 on 2018-04-15
As I read the man page '.y' would be treated as a 'regular expression' and match any package with a 'y' in the name, however it may also expand to match command line options.

---

### Post by mc4man on 2018-04-15
> **rsteinmetz70112 said:**
> As I read the man page '.y' would be treated as a 'regular expression' and match any package with a 'y' in the name, however it may also expand to match command line options.
I think you're correct about the 'regular expression and match any package..' If I was to go .n or .l it's even worse than .y
Even though many of the 1445 to be removed here don't have y they probably had depends on a package that did have y in the name.

It could & most likely is that -s  simulation skips the the confirmation, not y expanded.

---

### Post by mc4man on 2018-04-15
So based on rsteinmetz70112's comment (which is pretty much correct), if you actually executed that command then you would have removed packages with a y in it & any that depend on the removed packages.
(- which packages with a y is unclear as it's a autoremove command, somehow I think marked automatically installed still plays a part.

On the default 16.04 server install there are only 20 packages with a y in it  (compared to the Desktop 16.04.4 default of 300 give or take.

See if some of the below are still installed, (grabbing 5 of the 20 at random
libsystemd0
libgcrypt20
init-system-helpers
busybox-initramfs
libpython3.5-minimal


Edit: so for example if I install a package with virtually no dependencies & y in name (yale), running the command does not cause it to be removed. However if I mark yale as automatically installed it does get removed.
At the end of the doesn't much matter, using .a letter is certainly a poor idea.

---

### Post by rsteinmetz70112 on 2018-05-02
You know I think this is probably a bug since autoremove shouldn't require any arguments.

---

### Post by jeo7 on 2018-05-05
I made the mistake of using autoremove several years ago on 12.04. It removed a lot of programs that I didn't want removed including several desktop environments that I wanted to keep. I learned the hard way not to use it.

---

