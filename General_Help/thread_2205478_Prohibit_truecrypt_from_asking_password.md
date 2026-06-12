---
title: "Prohibit truecrypt from asking password"
date: 2014-02-14
forum: General Help
---

### Post by c2tarun on 2014-02-14
Hi friends, I am writing a backup script which will ask password from user and then transfer it to truecrypt to mount the ecryption file volume. Problem is in case user entered wrong password truecrypt is asking for password instead of my script. I don't want that, how can I disable truecrypt asking password?
here is my code snippet. [http://paste.ubuntu.com/6930140/](http://paste.ubuntu.com/6930140/)

---

### Post by TheFu on 2014-02-14
Putting a password on the command line like that is not secure. Everyone can see it in the process table listing using **ps**.  I looked through the [http://www.truecrypt.org/docs/command-line-usage](http://www.truecrypt.org/docs/command-line-usage) page and didn't see a secure way to do what it needed. I'm surprised they don't support passing in a filename or environment variable for this.

Have you tried checking the return code from the truecrypt call? If it is non-zero, that should mean there is an issue. print an error and exit.

To avoid the entire password-on-the-command-line issue, I'd create a new UNIX group and put anyone who should have access in that group and make the program with the password inside have execute, but not read access permissions. I don't think you can script it unless a language that can be compiled to binary is used like perl.

update ... 
The more I think about this, the more using some other backup tool that supports encryption makes more sense. Duplicty with GUI front-end DejaDup or Duplicati would be where I started.

Or if truecrypt source is available, adding the code to use a password file and/or environment variable shouldn't be too hard for any C programmer.

---

### Post by c2tarun on 2014-02-14
> **TheFu said:**
> Putting a password on the command line like that is not secure. Everyone can see it in the process table listing using **ps**.
I am using zenity to input password from user and then pass it to the command using a variable. Is this was also not secure?

> Have you tried checking the return code from the truecrypt call? If it is non-zero, that should mean there is an issue. print an error and exit.
Yeah I tried, return code is returning 0 if correct password and 1 if wrong password. But the problem is if I enter wrong password in zenity and pass it to truecrypt then truecrypt will check whether password is correct or not. In case of incorrect password truecrypt will continue in a loop and ask for password again and will not return anything until I enter correct password or press cancel in truecrypt pop-up.

> To avoid the entire password-on-the-command-line issue, I'd create a new UNIX group and put anyone who should have access in that group and make the program with the password inside have execute, but not read access permissions. I don't think you can script it unless a language that can be compiled to binary is used like perl.
This sounds complicate but better than the way I am doing it. I'll try this in version 2.0.

> update ... 
The more I think about this, the more using some other backup tool that supports encryption makes more sense. Duplicty with GUI front-end DejaDup or Duplicati would be where I started.

I tried DejaDup, I don't like the way it creates backup. I have to use dejadup to restore the backup. Ubuntu is my primary OS but I want to reuse backups on Windows and Mac as well. Duplicati also being a UI backup tool will be more or less same as deja dup. 
Rsync will simply sync all my files and will do that incrementally ;) so in case if I need any one file I'll just go there and copy it, rather than restoring whole backup.
Also my backup system is slightly different than normal backups. I am not encrypting everything. I am just encrypting my pictures and my personal documents. Rest other stuffs like, music, ebooks, wallpapers etc. I am not encrypting them. So the script I am writing will create encrypted backup of my personal files and create normal backup of other files. In normal backup also there are some tweaks. I found rsync more flexible for me. :)
Also I want to automate backup process, so that whenever I insert my HDD it ask me whether I want to start backup or not. If I press yes then it backsup otherwise wait for next time.

> Or if truecrypt source is available, adding the code to use a password file and/or environment variable shouldn't be too hard for any C programmer.
I don't think truecrypt is open source, also it would be a lot of work just for a simple backup task :)

_Solution to my problem:_ I converted my password to hashcode and I am comparing hashcode of entered password.

[Here]("http://paste.ubuntu.com/6934760/") is the script that I created for me: [http://paste.ubuntu.com/6934760/](http://paste.ubuntu.com/6934760/)
Now I have to configure it to start in udev.

One little help please, this is the first time I am scripting in bash. So I might have followed some poor and some very poor coding practice. If you see one, please please tell me. I'll surely improve quality of my code.

---

### Post by TheFu on 2014-02-15
Chances are that storing that hash is breaking your truecrypt security. Just sayin'.   

However, it is better than nothing and certainly better than storing the password in a file in plaintext. Definitely lock that file down.  If the storage holding this stuff isn't encrypted, it doesn't matter anyway for a determined cracker ... and it turns out there is an attack that works against nearly whole-drive encrypted Linux and Windows systems when physical access is available. Physical access means game-over, even for encrypted stuff, unless extreme care is taken that most people - even me - are unwilling to take. It is just too inconvenient to always carry a crypto-card, especially for servers that are 500 miles away and need to be rebooted.

There are many scripting "best practice" guides available. No need for me to repeat those things. If you can find or see Michael Porter's Bulletproof Bash presentation - highly recommended.  I don't think he makes the slides available anywhere.  All programs need to have a full path, do not trust the PATH environment.

I've never used Zenity. Don't have an opinion about the security of it - but passing parameters on the command line means anyone with access to the process table (everyone) can see those options.

---

