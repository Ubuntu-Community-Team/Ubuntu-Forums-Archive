---
title: "How to load caja and pluma from command line escallated as root? (NOT SUDO!!)"
date: 2022-07-02
forum: General Help
---

### Post by josh77 on 2022-07-02
Edit, this is a bad idea and a security risk as described by a helpful user below. I will modify my behavior as a result of this knowledge. (and completely re-install to wipe any problems)
-----------------------------------------------------
It is inconvenient to not be able to load caja and pluma while escalated to root.

Here is an example:

```
root@anon:~# caja&
[1] 13215
root@anon:~# Could not parse arguments: Cannot open display:
```

Now you may say "this is unsafe", to that I say I understand the risks and respectfully wish to do as I like. I've been using this method for a decade in CentOS with no issues.

You may ask, why not simply use sudo?

I want a separate password for certain tasks which is not my main account password, and it is simply faster and more efficient to run them from an open terminal which is escalated to root.


I have scoured the internet looking for answers, there are maybe a dozen posts over the past 10 years, with none of the solutions working at this time.


Anyone gotten this working for ubuntu 20?

Thanks

---

### Post by #&amp;thj^% on 2022-07-02
Knowing the risks already, I use:
```
pkexec caja
```
and for pluma:
```
sudo -H pluma
```
You can run it without the "**-H**" but I don't advise it, just my old ways of doing it.

---

### Post by Holger_Gehrke on 2022-07-02
The right answer to this depends quite a bit on the display server you're using. I can't help you if you use Wayland since I don't have any experience with it - I'm using XUbuntu and XFCE doesn't run with Wayland yet. From what I read on the net Wayland is not very friendly to applications running as root, although the xwayland compatibility system should allow you to use xhost ...

Having 'root' as an actual user capable of logging in is not a good idea. It simplifies any intruders life immensely to only have to guess the password and not both the username and the password. AFAIK Ubuntu was the first distribution to have root incapable of logging in and enforcing the use of sudo. You can get a shell with root abilities with 'sudo -i'. sudo gives you very fine grained control over who is allowed to do what through the file /etc/sudoers. There's a whole man page for that file, and it's essential reading ...

X11 has it's own security mechanisms in place. It won't allow graphical applications to connect to it unless they are run by a user authorized to use the display. You can use 'xhost +si:localuser:' with a username after the colon to allow a user to connect to the display. Run the same command with a '-' instead of the '+' to remove a user from the access control list. 

An alternative would be using the Midnight Commander (mc) in a terminal as root; mc is a terminal file manager that behaves similar to the old Norton Commander for MS-DOS.

For running an editor - like pluma - to edit system wide configuration files, setting and exporting EDITOR and running 'sudoedit' is probably safer and better. That way the editor isn't run as root; sudoedit makes a copy of the file, runs your editor with the copy and copies the file back if any changes were made. Only the copying is done with elevated privileges.

Holger

---

### Post by TheFu on 2022-07-02
Ubuntu isn't CentOS.  sudo has different compiled options.  Xorg has fairly weenie security and overriding it, which is what you need to do with this will open up the logged in userid for other attacks.  But  since you already know these things and it is your machine. Do what you like.

We used to screw with people who allowed the xorg settings necessary to run GUI programs under a different userid, but we could have done much evil, like capturing all keystrokes and sending them anywhere we liked in the world i.e. a keylogger. With just a little effort, creating a tool that does this wouldn't be hard, I'm sorry to say. 

However, when you cannot log into the system anymore with a DE/GUI, just know it was likely caused by this choice today.  The fix is to have your userid take ownership of all files in your $HOME. Not hard, if you have ssh setup, since the login loop would be for GUIs only.

+1 for using sudoedit.  BTW, this works on centOS too.

---

### Post by #&amp;thj^% on 2022-07-02
+2 for sudoedit
```
export PROMPT_COMMAND=_prompt_command
EDITOR="/bin/xed"
export EDITOR
export LC_TIME=en_US.utf8
```
My editor is not pluma obviously. ;)
As TheFu said It pretty much works on most Linux OS's

---

### Post by josh77 on 2022-07-06
Thank you kind sage (**[COLOR=#000000]TheFu[/COLOR]**[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")), I will take that to heart and change my insecure ways.

---

### Post by josh77 on 2022-07-06
No way to delete posts here? Sad.

---

### Post by TheFu on 2022-07-06
> **josh77 said:**
> No way to delete posts here? Sad.

There is someone else who can learn from all our mistakes.  Most of my advice comes either from making mistakes or being coached by smarter people than I about something that seems reasonable until looking a little deeper shows critical issues that are caused.  It really is sad how often I ignored those more knowledgeable people and had to learn things the hard way, for myself.

I still make foolish mistakes, almost daily and my networks aren't all perfect either. There's what we have and what we desire based on decades of knowledge. Those seldom align perfectly for anyone.  ;)

---

### Post by QIII on 2022-07-07
@Josh77

Finding your answer and then wiping it away from everyone else's view would be rather selfish, would it not?

See my signature.

---

