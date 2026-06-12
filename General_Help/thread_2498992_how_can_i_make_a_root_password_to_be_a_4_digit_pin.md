---
title: "how can i make a root password to be a 4 digit pin code?"
date: 2024-07-07
forum: General Help
---

### Post by ronjjjg8885 on 2024-07-07
i've a media center computer that i want a short password to, but ubuntu won't allow this.. is there a way to fix this?
i use a remote control and it is not comfortable to type a long password in it..

tnx

---

### Post by Holger_Gehrke on 2024-07-07
I don't know about the password for root since the root user is not allowed to login directly on Ubuntu for security reasons, but you can set a password for any other user from the command line using the command 'passwd'. While the graphical tool to set passwords enforces a minimum length (6 characters on Xubuntu 22.04) passwd doesn't. In a test i could change the password for my secondary account to a single character.

Holger

---

### Post by HermanAB on 2024-07-07
I know you don’t want to hear this, but don’t set a short 4 letter password.  You will be sorry eventually and you will have to reinstall to get rid of the script kiddies.

You should use at least a 12 digit password to keep scoundrels out.

---

### Post by TheFu on 2024-07-07
I have my media center playback devices (not the server), automatically login and start the software.  The userid is "kodi" and the setup just has a check-box.

If you want to set a password for a user that doesn't meet the built-in minimim standards, usually, typing the non-compliant password 3 times will force it.
```
$ passwd 
Old Password: xxxxxx
New Password: yyyyyy
To short, again?  yyyyyy
To short, again?  yyyyyy
$
```
And that's it.  I don't know the exact prompts, but something like that.

For systems on the internet, passwords should be over 12 characters and never allow password-based logins over the internet, always use cert or key-based credentials over the internet.  As everyone here probably knows, setting up ssh-keys is just 2 commands from the client.  It is both more secure AND more convenient.  That never happens, except with ssh-keys.

---

### Post by currentshaft on 2024-07-07
> **HermanAB said:**
> I know you don’t want to hear this, but don’t set a short 4 letter password.  You will be sorry eventually and you will have to reinstall to get rid of the script kiddies.

You should use at least a 12 digit password to keep scoundrels out.

Stop the FUD, please.

There are appropriate uses of short passwords, even no password, even no encryption under certain conditions. An example of that would be a shared media PC inside a home which is both physically controlled and is behind a NAT.

OP: change the password as root, it will bypass PAM policy enforcing a minimum requirement.

---

### Post by ronjjjg8885 on 2024-07-07
tnx i will use the command

the thing is that when the computer goes to a suspend mode it requiring me the password after waking the computer..
is there a fix for that that will make it not ask me for password?


so what you are saying is that if the computer is connected to the internet i will need a 12 character good password?


the other issue are the updates that also need a password..

i've a remote like that..
[https://duckduckgo.com/?q=%22Pepper+Jobs+W10+GYRO+Air+TV+Remote%2CQWERTY+Keyboard+Fly+Mouse+for+Win+11%2F10%22&t=lm&ia=web](https://duckduckgo.com/?q=%22Pepper+Jobs+W10+GYRO+Air+TV+Remote%2CQWERTY+Keyboard+Fly+Mouse+for+Win+11%2F10%22&t=lm&ia=web)
not easy to type with it..

while using windows i never needed a password once after the initial logging in.
on ubuntu i set it to not ask for a password upon logging in but there are other occasios when i you do need it..

i wish it was simpler

---

### Post by HermanAB on 2024-07-07
I wish it was FUD. I’ve been around the block a few times.

---

### Post by yancek on 2024-07-07
>  the other issue are the updates that also need a password.

Updates are modifying/adding to system files which require root/sudo permissions.  If you don't have any type security such as a password, anyone with physical access can do anything they want including delete your data.  If you like the windows way of doing things why not use it?  Did you search online how to disable password request after suspend on Ubuntu?  I found  a number of sites  but some are for specific release versions of Ubuntu and may not work on other versions.  Since you haven't indicated which Ubuntu you are using, just put that into your search.

---

### Post by dragonfly41 on 2024-07-07
> [COLOR=#000000]i wish it was simpler
[/COLOR]On the subject of password management I've recently started using a Proton account and I find the companion Proton Pass to be very useful.  But Proton structure takes a bit of getting used to. I'm still learning.

---

### Post by deadflowr on 2024-07-07
> the thing is that when the computer goes to a suspend mode it requiring me the password after waking the computer..
is there a fix for that that will make it not ask me for password?


Settings > Privacy and Security > Toggle Lock Screen on Suspend to off.
And also toggle Automatic Screen Locking to off as well.

---

### Post by TheFu on 2024-07-08
> **ronjjjg8885 said:**
>  
i wish it was simpler

I do all the management of my media center over ssh, so that happens from a real computer.
Also, it is possible to allow specific users to run specific commands with specific options without requiring authentication.  Learn about the sudoers file.  If you do this, don't allow just any commands, nor random options to those commands, but there is little reason NOT to allow the main user to run 
```
/usr/bin/sudo   /usr/bin/apt-get   update
```
and 
```
/usr/bin/sudo   /usr/bin/apt-get   upgrade
```
without authentication.  Just be certain you don't allow the userid to edit any system files or run any programs that can edit system files.
Note how I specified the full path to the exact programs I want to allow to run without further authentication.  That's important.

While you can take this to the next level by setting up a cronjob as root to run those 2 commands weekly, I'd strongly suggest you do not do that.  I've been burned a few times by terrible updates that removed 1 type of program and installed a different type due to terrible dependencies.  Took me about 4 hours to figure out what happened.  Had I been watching the updates, like I do now, I would have seen one of the critical programs being uninstalled and stopped everything right then.  I still use a script to update all my systems, but that script is run while I watch it.  That process has saved me some issues a few times over the decades.  This script uses ssh into each different system, then runs the commands, logging everything that happens along the way to a single file.  I don't parallelize these updates.  Generally, it takes less than 3 minutes to patch 20 systems, some of them are remote.

---

### Post by ronjjjg8885 on 2024-07-09
windows is collecting data. this is why i don't use it..
i also want to promote open source.
tnx

---

### Post by TheFu on 2024-07-09
> **ronjjjg8885 said:**
> windows is collecting data. this is why i don't use it..
i also want to promote open source.
tnx

MSFT has the power to ignore or redirect people looking into their security failures.  That concerns me greatly: 
[https://www.propublica.org/article/cyber-safety-board-never-investigated-solarwinds-breach-microsoft](https://www.propublica.org/article/cyber-safety-board-never-investigated-solarwinds-breach-microsoft)
is one example, but there are others that were much worse for people running MS-AD - to a point that AD was a joke for a few years and the people who knew about it were prevented from discussing it by the Feds.  After 2 yrs of knowing the issue, MSFT hadn't corrected the issue. It was only the possible lifting of that gag order that finally got MSFT to do something.  Even then, they tried to delay, delay, delay.

Canonical collected data in the 2016 timeframe.  All local searches were sent to Amazon, for example.  And if you think there isn't a kickback from the main browser installed on ubuntu from google for all the search traffic, you'd be wrong.  Google is going to get their data, regardless, whenever we use their services. Obviously, they will prevent ads and track us in that same browser session, at a minimum.  We need an "opt in" law to prevent any data from causal uses who never login to google from being stored, ever.  The current opt-out method requires logging in, which defeats the purpose.

---

### Post by ronjjjg8885 on 2024-07-11
hello
i'm not sure what you want to say..

---

### Post by currentshaft on 2024-07-11
> **ronjjjg8885 said:**
> hello
i'm not sure what you want to say..

How about, "thank you for answering my question and for explaining how to do this."?

---

### Post by ronjjjg8885 on 2024-07-21
> **currentshaft said:**
> How about, "thank you for answering my question and for explaining how to do this."?
thanks
i usually saying it but i havn't noticed i didn't

---

### Post by him610 on 2024-07-21
It has been a long time and I have forgotten what many acronyms once meant. For anyone still wondering about *FUD* -
> FUD is an abbreviation for "fear, uncertainty, and doubt". It's a manipulative propaganda tactic used to influence perceptions by spreading negative, false, or dubious information. FUD can be used in many areas, including sales, marketing, public relations, politics, polling, and cults. It can also be used to manipulate investor and consumer emotions, often in the form of rumors, false news stories, or adverse facts. 


---

