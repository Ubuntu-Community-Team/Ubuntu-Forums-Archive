---
title: "apt errors when updating"
date: 2017-02-03
forum: General Help
---

### Post by AwaitingUserInput on 2017-02-03
I am trying to install the Brave web browser via their private package archive. When I first got GPG key errors, I thought I had added the keys incorrectly, so I re-typed the commands to add the key and repository. Now it gives me even more errors about the repository being listed twice. How can I clean this up and have the repository in my software sources, so that the Brave browser updates itself when I do my normal software updates?

Here's what I did first, from the [Brave installation documentation]("https://github.com/brave/browser-laptop/blob/master/docs/linuxInstall.md"). I did this twice, which must be why apt is telling me it's configured multiple times.
```

$ curl https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc | sudo apt-key add -
$ echo "deb [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt `lsb_release -sc` main" | sudo tee -a /etc/apt/sources.list.d/brave-`lsb_release -sc`.list
```

Here is some of the output from  sudo apt update:
```

Reading package lists... Done                                                
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1
W: GPG error: https://s3-us-west-2.amazonaws.com/brave-apt xenial InRelease: The following signatures couldn't be verified because the public key is not availe: NO_PUBKEY 6ED19DBB448EEE6C
E: The repository 'https://s3-us-west-2.amazonaws.com/brave-apt xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1      
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1        
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1 
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1    
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1   
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:54 and /etc/apt/sources.list.d/brave-xenial.list:1  
```

Questions:
[LIST=1]
[*]How do I correctly add the GPG key? 
[*]What do I need to do to get rid of the "...is configured multiple times" error? 
[/LIST]

I'm running Kubuntu 16.04

TIA!

---

### Post by mc4man on 2017-02-03
When you ran the curl command did you enter your password after it downloaded & receive an "OK"?
It may not be exactly obvious, (blue) about the password, here was on same line.. - ex.
```
:~$ curl https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc | sudo apt-key add -
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1828  100  1828    0     0   1084      0  0:00:01  0:00:01 --:--:--  1084[COLOR="#000080"][sudo] password for doug:[/COLOR] 

OK
```
Then it would show in apt-key list, ex.
```
:~$ apt-key list |grep Brave
uid                  Brave Software (We're reinventing the browser as a user-first platform for speed and privacy) <support@brave.com>

```

---

### Post by AwaitingUserInput on 2017-02-04
Thanks so much! I did what you said and the key now shows up when I do the *apt-key list*. I also don't get the errors that I was getting when I did *apt update*.

I am still getting the "...is configured multiple times" error, but I will probably start a new thread for that and mark this one "solved" to keep this thread simple.

---

