---
title: "Ubuntu tweak stop working"
date: 2014-09-20
forum: General Help
---

### Post by offir on 2014-09-20
I'm using Ubuntu 14.04 and Cairo Dock

ubuntu tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) stop working a failed installation attempt of mono

i use this link as a guide [http://www.rocko.me/install-mono-3-4-ubuntu/](http://www.rocko.me/install-mono-3-4-ubuntu/)

after the first command 
```
sudu apt-get purge mono-*
```
Everything is destroyed (here link with details) [http://ubuntuforums.org/showthread.php?t=2242805&p=13114967#post13114967](http://ubuntuforums.org/showthread.php?t=2242805&p=13114967#post13114967)
i was told by Impavidus to use this command can fix it [http://ubuntuforums.org/showthread.php?t=2242805&p=13115034#post13115034](http://ubuntuforums.org/showthread.php?t=2242805&p=13115034#post13115034)
```
sudo apt-get install light-themes ubuntu-mono
```
and it did


but ubuntu tweak stop working  
Every time I click on the program icon 
Nothing happens
i was told by mc4man to use this command in terminal [http://ubuntuforums.org/showthread.php?t=2242943&p=13116466#post13116466](http://ubuntuforums.org/showthread.php?t=2242943&p=13116466#post13116466)

```
ubuntu-tweak
```
and 
```
ubuntu-tweak -d
```






[SIZE=3][B]

This is what I got [/B][/SIZE]


```
ubuntu-tweak
```
give this
```
** (ubuntu-tweak:17548): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-gEtMfgB3Sa: Connection refused
Attempt to unlock mutex that was not locked
Aborted (core dumped)
```


```
ubuntu-tweak -d
```
give this
```
** (ubuntu-tweak:17666): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-gEtMfgB3Sa: Connection refused
[Launcher][DEBUG] Distribution: Ubuntu 14.04 trusty
Application: Ubuntu Tweak 0.8.7-1~trusty2
Desktop:cairo-dock (ubuntu-tweak:84)
Attempt to unlock mutex that was not locked
Aborted (core dumped)
```



I do not know what that means
Or how to fix it ](*,)

---

### Post by offir on 2014-09-21
no one know how to fix it ?
or what this means ?

---

### Post by offir on 2014-10-20
No one come across this ?

---

### Post by sudodus on 2014-10-20
Ubuntu Tweak works for me in 14.04.1 LTS, but I have not installed ***mono***. Maybe if someone reading this will recognize ***mutex***, we'll get closer to a solution.

Have you tried to purge ubuntu-tweak (and reinstall it)?

---

### Post by offir on 2014-10-24
> 
Have you tried to purge ubuntu-tweak (and reinstall it)? 

yes i tried
same result

---

### Post by offir on 2015-01-17
I have to run this software
How do I fix it


I tried to write in developer Web page
But What I write
Not saved


If I can not fix it
My only option in this format and reinstall the system

---

### Post by sudodus on 2015-01-17
The beginning of the thread was long ago. Please tell us what is your ***current*** problem - with as many details as possible :-)

---

### Post by offir on 2015-01-17
Exactly the same situation
Since I do not have the Knowledge - how to solve it
So I did not try

I tried several times to find information in the software creates blog no success


Here is the output from now

```
ubuntu-tweak
```

```
** (ubuntu-tweak:6079): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-Rx64R5ywG6: Connection refused
Attempt to unlock mutex that was not locked
Aborted (core dumped)

```


and 



```
ubuntu-tweak -d
```

```
** (ubuntu-tweak:6053): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-Rx64R5ywG6: Connection refused
[Launcher][DEBUG] Distribution: Ubuntu 14.04 trusty
Application: Ubuntu Tweak 0.8.8-1~trusty1
Desktop:cairo-dock (ubuntu-tweak:84)
Attempt to unlock mutex that was not locked
Aborted (core dumped)


```

---

### Post by offir on 2015-01-17
From what I can see only one thing has changed
the last word

old code
```
Failed to connect to socket /tmp/dbus-gEtMfgB3Sa
```



New code
```
Failed to connect to socket /tmp/dbus-Rx64R5ywG6
```

---

### Post by sudodus on 2015-01-17
That difference is only a temporary file, that is created with a random name, so no real difference.

Maybe dbus is creating the problem. Do you need dbus? Are you switching between different languages?

Do you need mono? Do you need ubuntu-tweak?

Maybe there is some lack of compatibility between mono and ubuntu-tweak.

What do you want to do with ubuntu-tweak? Can it be done with some other tool? - I think this might be worth looking into as a good alternative.

Or can you remove mono, install and run ubuntu-tweak to do what you want, and then remove ubuntu-tweak and install mono again? - I don't know if it would work, but it might be worth trying.

---

### Post by offir on 2015-01-17
> Maybe dbus is creating the problem. Do you need dbus? Are you switching between different languages?

yes. between English and Hebrew



> Do you need ubuntu-tweak?

yes. I use him to change some settings
Of the programs or the system it is more convenient for me


> Do you need mono?

yes. I came across several sites that require Silverlight
And it sends me to install Mono

> Maybe there is some lack of compatibility between mono and ubuntu-tweak.

I do not know
Currently
Mono is not installed
Because I got into trouble with his installation

---

### Post by sudodus on 2015-01-17
Maybe these mails (from the Lubuntu mailing list, [EMAIL="lubuntu-users@lists.ubuntu.com"]lubuntu-users@lists.ubuntu.com[/EMAIL]) can help you at least get rid of dbus and still have a tool to switch between languages.

> On Mon, Jan 12, 2015 at 12:02 PM, Marc Tremblay wrote:[INDENT]I did some research and found a temporary solution that involved changing
the Keyboard input method from IBUS to none. This essentially resolved the
issue in the browser but also caused another problem in that we are now
unable to switch our keyboard from English to French. We are a bilingual
school board so French is a must.
[/INDENT]

There are other input methods out there you could try instead. I use
`uim` but `fcitx` is very popular.

We discussed in the past getting rid of `ibus` and I'm still not sure
why we don't. Their developers are extremely unhelpful and
unresponsive.

-- 
@wxl
Lubuntu Release Manager, Head of QA
Ubuntu PPC Point of Contact
Ubuntu Oregon LoCo Team Leader


> 
On Mon, Jan 12, 2015 at 12:11 PM, Marc Tremblay wrote:[INDENT]Can I simply install uim or fctx through the terminal?
[/INDENT]

Yep. &#9786;

Then set it as default input method.

You should check to make sure that there's no mention of ibus in
`update-alternatives --get-selections`. It seems that the way it keeps
track of input methods is by locale, so make sure that xinput-fr_CA
and xinput-en_CA (I think I got that right?) point to your input
manager.

-- 
@wxl
Lubuntu Release Manager, Head of QA
Ubuntu PPC Point of Contact
Ubuntu Oregon LoCo Team Leader




What settings do you want to change? Maybe we can help you to find another tool than ubuntu-tweak or even to make a shell-script or alias that will do it for you.

---

### Post by mc4man on 2015-01-17
libgtk2.0-0 had an issue that caused some apps to fail with "Attempt to unlock mutex that was not locked" but that was starting with 2.24.24 (utopic)
various - 
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=763690](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=763690)
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1376530](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1376530)
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1374030](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1374030)

The version in 14.04 should be ok - what's this show?
```
apt-cache policy libgtk2.0-0
```

---

### Post by offir on 2015-01-17
```
apt-cache policy libgtk2.0-0
```
Do try it on my computer ?

What does it do ?

---

### Post by mc4man on 2015-01-17
> **offir said:**
> ```
apt-cache policy libgtk2.0-0
```
Do try it on my computer ?

What does it do ?
Shows what version of libgtk2.0 is installed

---

### Post by offir on 2015-01-17
```
libgtk2.0-0:
  Installed: 2.24.23-0ubuntu1.1
  Candidate: 2.24.23-0ubuntu1.1
  Version table:
 *** 2.24.23-0ubuntu1.1 0
        500 http://il.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.24.23-0ubuntu1 0
        500 http://il.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by offir on 2015-01-23
is there a way to fix the problem ?

---

### Post by sudodus on 2015-01-23
I'm sorry, but I haven't got any good ideas how to solve your problem. Let us hope someone else can add something new into your thread.

---

### Post by offir on 2015-03-11
The message has changed

Now when I write this
```
ubuntu-tweak -d

```

i get this 
```
[Launcher][DEBUG] Distribution: Ubuntu 14.04 trusty
Application: Ubuntu Tweak 0.8.8-1~trusty1
Desktop:cairo-dock (ubuntu-tweak:84)
Attempt to unlock mutex that was not locked
Aborted (core dumped)

```

---

### Post by mc4man on 2015-03-11
If you log in to a guest session does ubuntu-tweak work?  (guessing yes

Do you have choices when logging in, if so does it work in an ubuntu session?

You show this - 
> Desktop:cairo-dock (ubuntu-tweak:84)
Most users where the app runs  will show  - 
> Desktop:ubuntu (ubuntu-tweak:84)

---

### Post by dino99 on 2015-03-11
> **offir said:**
> The message has changed

Now when I write this
```
ubuntu-tweak -d

```

i get this 
```
[Launcher][DEBUG] Distribution: Ubuntu 14.04 trusty
Application: Ubuntu Tweak 0.8.8-1~trusty1
Desktop:cairo-dock (ubuntu-tweak:84)
Attempt to unlock mutex that was not locked
Aborted (core dumped)

```

is dist-upgrading an acceptable choice for you ?
maybe vivid or at least utopic which are better maintained now

---

### Post by offir on 2015-03-11
> **mc4man said:**
> If you log in to a guest session does ubuntu-tweak work?  (guessing yes

Do you have choices when logging in, if so does it work in an ubuntu session?

You show this -
 ```
 Desktop:cairo-dock (ubuntu-tweak:84) 
```

Most users where the app runs  will show
```
Desktop:ubuntu (ubuntu-tweak:84) 
```  -


I log out from the system
In the login screen where I write down the password
There is an option to choose
Between a desktop Ubuntu
And Cairo Dock Desktop

I tried them both

In both cases, ubuntu-tweak does not work

in Ubuntu Desktop the line is 
```
Desktop:ubuntu (ubuntu-tweak:84) 
```

in cairo-dock desktop the line is
```
 Desktop:cairo-dock (ubuntu-tweak:84) 
```




> is dist-upgrading an acceptable choice for you ?
maybe vivid or at least utopic which are better maintained now 
i know what is upgrading 
what is dist-upgrading ?  dist = Distribution ?
if so then no 
I prefer to stick with the current distribution

---

