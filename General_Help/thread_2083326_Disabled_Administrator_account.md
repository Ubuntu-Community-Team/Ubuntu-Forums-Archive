---
title: "Disabled Administrator account"
date: 2012-11-12
forum: General Help
---

### Post by jobsaditmate on 2012-11-12
Hi, firstly I know this is a silly thing to have done but equally, I am quite amazed that the system would allow me to "Disable" the only Administrator account.  Secondly, although I have got as far as something called "Grub" and typed in "passwd" I have no real experience of it, and feel out of my depth in the Root thingy.

The result so far is: "passwd:Athentication token manipulation error" and now I am really stuck.  I am not even sure - if it came to it - how I could just reload the operating system and sacrifice all my stuff.

I know the Admin password still, it is just that I cannot unlock the admin account because, of course, the system will not now accept the only disabled Admin's authentication password.

Please help!  Preferably with a cut and paste code solution for the Root thing as I do now know how to get there.

I am stuck currently logging in as a guest.

Thanks in anticipation

Jobs :confused:

---

### Post by Abhinav Kumar on 2012-11-12
Hi jobsaditmate,
Can you please be a bit more clearer on what you are trying to do ?

Regards,
Abhinav

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> Hi, firstly I know this is a silly thing to have done but equally, I am quite amazed that the system would allow me to "Disable" the only Administrator account.  Secondly, although I have got as far as something called "Grub" and typed in "passwd" I have no real experience of it, and feel out of my depth in the Root thingy.

The result so far is: "passwd:Athentication token manipulation error" and now I am really stuck.  I am not even sure - if it came to it - how I could just reload the operating system and sacrifice all my stuff.

I know the Admin password still, it is just that I cannot unlock the admin account because, of course, the system will not now accept the only disabled Admin's authentication password.

Please help!  Preferably with a cut and paste code solution for the Root thing as I do now know how to get there.

I am stuck currently logging in as a guest.

Thanks in anticipation

Jobs :confused:

From how you describe it it sounds like your user is not now in the admin group. See this how to fix it. Either print it out or just write down the relevant bits.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by jobsaditmate on 2012-11-12
I have "disabled" the only the only administration account on my Ubuntu operating system software.

I need to restore the administration account, in other words I need to unlock it.

I still have the password for it but it will not accept it because the account is disabled.

I am current logged in as a guest to the system

Is that any clearer?

Jobs

---

### Post by jobsaditmate on 2012-11-12
Thanks Philinix.   Wish me luck! :)

---

### Post by jobsaditmate on 2012-11-12
Got nowhere with that Phil

mount -o rw, remount

didn't work and

add username admin

(My username used of course) came back with only one or two usernames allowed

are user names case sensitive?

Jobs

---

### Post by jobsaditmate on 2012-11-12
To try and be clear: 

the only admin account on the system is there, it is just disabled. 

Due to it being disabled it is unable to enable itself.  

I cannot do it through guest account as it asks disabled admin to authenticate the change and then does not accept admins password.

:confused:

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> Got nowhere with that Phil

mount -o rw, remount

didn't work and

add username admin

(My username used of course) came back with only one or two usernames allowed

are user names case sensitive?

Jobs

ok you missed off the / in the mount command. "/" represents the root partition. 

Your username should be typed in exactly as you know it.

type is ls /home to show your username. Thats a lower case L byt the way.

As the link describes you have to do this from recovery mode which has root access.

---

### Post by jobsaditmate on 2012-11-12
I did put / as described but left it out of reply sorry.

---

### Post by jobsaditmate on 2012-11-12
Do this:

> type is ls /home to show your username. Thats a lower case L byt the way.

at the root prompt presumably?

---

### Post by jobsaditmate on 2012-11-12
running 12.04LTS btw

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> Do this:

at the root prompt presumably?

Yes. I'm not sure of the result in the guest session. It will work though. Try it out. ls just means List directories.

[edit] in a guest session you get permission denied.

---

### Post by jobsaditmate on 2012-11-12
response from: mount -o rw,remount /

is:"mount: special device remount does not exist"

---

### Post by steeldriver on 2012-11-12
> **jobsaditmate said:**
> response from: mount -o rw,remount /

is:"mount: special device remount does not exist"

... it sounds like you are leaving a space between the 'rw' and the 'remount' - you need to type it EXACTLY as shown with ONLY a comma between the 2 options

```
mount -o **rw,remount** /
```

---

### Post by jobsaditmate on 2012-11-12
done with no space between rw,remount

when I did the "adduser username admin" it said there was no group called admin

I tried adduser username and it said user already exists.  I seem to need a command to enable the disabled admin account?

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> response from: mount -o rw,remount /

is:"mount: special device remount does not exist"

I'm on 12.10 and that command works.

try this ```
mount -o remount,rw -n /
```

then check to see if root is rw with ```
mount -l
```

Then try to add your user to admin.

---

### Post by steeldriver on 2012-11-12
AFAIK the default admin group is 'sudo' in recent releases - it sounds like your filesystem is successfully remounted with write permissions so you can do

```
gpasswd --add *yourusername* sudo
```

---

### Post by philinux on 2012-11-12
> **steeldriver said:**
> AFAIK the default admin group is 'sudo' in recent releases - it sounds like your filesystem is successfully remounted with write permissions so you can do

```
gpasswd --add *yourusername* sudo
```

Indeed from 12.04, thanks for that. Looks like psychocats needs an edit.

[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

[edit] I've posted in the psychocats thread. [http://ubuntuforums.org/showpost.php?p=12350258&postcount=633](http://ubuntuforums.org/showpost.php?p=12350258&postcount=633)

---

### Post by jobsaditmate on 2012-11-12
got the following:
adding user [username] to group sudo
gpasswd: cannot lock/etc/group; try again later

:confused:

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> got the following:
adding user [username] to group sudo
gpasswd: cannot lock/etc/group; try again later

:confused:

I can only offer this.

[http://askubuntu.com/questions/84277/cannot-lock-etc-group-in-recovery-mode](http://askubuntu.com/questions/84277/cannot-lock-etc-group-in-recovery-mode)

It would appear your root is still read only or ro. It needs to be rw.

---

### Post by jobsaditmate on 2012-11-12
"whoami" answer:

root

"cat /proc/mounts" answer

rootfs/rootfs rw 0 0

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> "whoami" answer:

root

"cat /proc/mounts" answer

rootfs/rootfs rw 0 0

Thats good so you need to start again in recovery, make root rw, check that it's rw and then

adduser username root

---

### Post by jobsaditmate on 2012-11-12
had another go after checking root and it seems to be in rw
> 
adding '[username]' to group 'root'
adding '[username]' to group 'root'
gpassword: cannot lock /etc/group;try again later
adduser: '/usr/bin/gpassword - a [username] root' returned error code 1. Exiting

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> had another go after checking root and it seems to be in rw

If root really is rw then it sounds like there's a lock file preventing you from adding your user to root. 

I'm not entirely sure which it is. It could be something like /etc/group.lock

In which case it needs deleting. Wait for someone else to chime in.

---

### Post by jobsaditmate on 2012-11-12
the problem started last night when logged in as admin i disabled my own admin account in setting ... user accounts so it is definitely locked - that seems to be the issue.

I am now downloading the 12.10 version with the idea of running it separately and putting this one on ice for a while until a solution becomes available.  Will that work do you think?

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> the problem started last night when logged in as admin i disabled my own admin account in setting ... user accounts so it is definitely locked - that seems to be the issue.

I am now downloading the 12.10 version with the idea of running it separately and putting this one on ice for a while until a solution becomes available.  Will that work do you think?

Good plan. Idea.

From the guest user do this and report back,

```
locate /etc/*.lock
```

---

### Post by jobsaditmate on 2012-11-12
cannot execute the install of new ubuntu.  Bang goes that idea then

---

### Post by jobsaditmate on 2012-11-12
result from your last:
> 
guest-im3vZs@stephen-Satellite-C650D:~$ locate /etc/*.lock
/etc/.pwd.lock
guest-im3vZs@stephen-Satellite-C650D:~$ 


---

### Post by steeldriver on 2012-11-12
Hi can we take a step back here

How exactly did you "disable" the account? if you did it through the  GUI User Accounts -> Password -> Disable then to re-enable from the recovery console the command you would need is

```
# usermod -U *yourusername*
```This is different from re-adding your user to the sudo (or admin) group, which I think is what we were all assuming you needed to do. FWIW 'usermod -U' works on the /etc/shadow file - removing the '!' ahead  of the encrypted password which is placed there when you mark the  account disabled - you can 'cat' your /etc/shadow file to see whether the password has a '!' in front of it

The /etc/.pwd.lock file *may* prevent you from doing that but let's see...

[Philinux I don't understand why the OP would want to add the user account to the root group - which in Ubuntu is root's user private group afaik - can you explain the reasoning behind suggesting that?]

---

### Post by philinux on 2012-11-12
Steeldriver,

Thanks for getting back.

If I made a mistake it's due to reading this.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Common_Infrastructure](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure.Common_Infrastructure)

Maybe I need more coffee.

---

### Post by jobsaditmate on 2012-11-12
put the kettle on then, I'll be back in a bit

---

### Post by JKyleOKC on 2012-11-12
Are you getting to the "root" prompt from the grub menu by selecting the "recovery" option? You can tell; if you are, you will get a black screen with white lettering and a prompt that ends with "#" instead of "$" and will already be logged in.

Once you get to this point, try the command "cat /etc/shadow" which will display the content of your "shadow" file that contains the password hashes. The very first line should start "root" and have a "!" character where the other lines have "*" as their second item. Find the line that starts with your user name and verify that it has "*" rather than "!" -- and if it has "!" then you will need to change it back. The easiest way to make the change is to type "gedit /etc/shadow" at the next prompt and use the text editor, but be extremely careful with it since it's quite easy to damage the system when logged in as root.

If you actually did have the system disable your account, this should enable it again. The "!" entry in the "shadow" file is what does the disabling. However if the "shadow" file doesn't show disabling, then what probably happened was removing you from the "sudo" group. In this case, the command suggested by Philinux should fix it by adding your account back to the group.

If you cannot get to the root prompt because of a lock condition, try searching the /var/run directory for the lock file. Also check your home directory, which would be /home/(your user name) and use the command "ls -a" to do the searching, so that it shows hidden files in addition to normal ones.

Hope this helps some!

---

### Post by jobsaditmate on 2012-11-12
Thanks Jkyle

Confirm there is the # at prompt

typed in cat/etc/shadow

got returned:

> bash: cat/etc/shadow no such file or directory

I didn't go on to the gedit and came back here

---

### Post by jobsaditmate on 2012-11-12
is that a space though between "cat" and "/edit/shadow" ?  If it is I didn't put the space in

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> is that a space though between "cat" and "/edit/shadow" ?  If it is I didn't put the space in

Yep needs a space.

Also gedit won't work as it's a gui file editor you'd have to use nano instead.

---

### Post by jobsaditmate on 2012-11-12
oh God Phil!  What's a nano?

---

### Post by JKyleOKC on 2012-11-12
"nano" is a text editor that works in the CLI. However the command that was suggested a few messages earlier than my post would be even simpler, and safer, to use.

Specifically, the "usermod" command from steeldriver!

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> oh God Phil!  What's a nano?

Just a command line text file editor. 

[http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/](http://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/)

It's invaluable when using the command line as you need to to fix things.

You only need to know this. Make the changes as indicated using nano then use ctrl o to save the file. Simples.

---

### Post by jobsaditmate on 2012-11-12
Ok well I got in there and changed the "!" to a "*" successfully.  Reboot when ok so I don't seem to have fragged the whole OS. But come log in it still wont accept the password and log me in as admin.  I went back to the /etc/shadow file and checked and it was still showing :*:

---

### Post by philinux on 2012-11-12
> **jobsaditmate said:**
> Ok well I got in there and changed the "!" to a "*" successfully.  Reboot when ok so I don't seem to have fragged the whole OS. But come log in it still wont accept the password and log me in as admin.  I went back to the /etc/shadow file and checked and it was still showing :*:

Well done i think.

So log in as normal. Is there any error when you try this as an example.

```
gksu gedit /etc/apt/sources.list
```

---

### Post by JKyleOKC on 2012-11-12
OK, take a look at /etc/group and find the line that starts with "sudo" to see whether your user name is anywhere on that same line. If not, use the command that Phil suggested originally to add yourself to that group and see whether that works...

If it is, though, I'm out of ideas!

---

### Post by philinux on 2012-11-12
For comparison this is mine. Jkyle I suppose one could use nano /etc/group from recovery to make any changes?

```
cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
**adm:x:4:phil**
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:phil
floppy:x:25:
tape:x:26:
**sudo:x:27:phil**
audio:x:29:pulse
dip:x:30:phil
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
**plugdev:x:46:phil**
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
bluetooth:x:106:
scanner:x:107:
colord:x:108:
**lpadmin:x:109:phil**
ssl-cert:x:110:
lightdm:x:111:
nopasswdlogin:x:112:
netdev:x:113:
whoopsie:x:114:
mlocate:x:115:
ssh:x:116:
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
philcb:x:1000:
**sambashare:x:124:phil**
ntp:x:125:
gdm:x:126:
```

---

### Post by steeldriver on 2012-11-12
With all due respect to my elders and betters, I really don't think it's a good idea for an inexperienced user to be making direct edits on the passwd/group files

I think if you edited the encrypted password field in /etc/shadow to *  (instead of just removing the leading ! from the previous encrypted  password or using usermod like I suggested) then the account will still  be disabled until you set a new valid password for it, i.e.

```
# passwd *yourusername*
```and follow the instructions

You can use

```
# id *username*
```to check whether the user's group memberships are as they should be and gpasswd from the recovery shell to fix them if necessary

---

### Post by philinux on 2012-11-12
> **steeldriver said:**
> With all due respect to my elders and betters, I really don't think it's a good idea for an inexperienced user to be making direct edits on the passwd/group files

I think if you edited the encrypted password field in /etc/shadow to *  (instead of just removing the leading ! from the previous encrypted  password or using usermod like I suggested) then the account will still  be disabled until you set a new valid password for it, i.e.

```
# passwd *yourusername*
```and follow the instructions

You can use

```
# id *username*
```to check whether the user's group memberships are as they should be and gpasswd from the recovery shell to fix them if necessary

I agree. I was suggesting a last resort scenario.

---

### Post by jobsaditmate on 2012-11-12
Ok done the passwd username

passwd: Authentication token manipulation error
passwd: password unchanged

I tried to copy that list phil but when I pasted it onto a message i couldn't get rid of all the freaking smiley faces it conjured up.  Is there a text only thing.  My 'code' didn't look like yours though

---

### Post by steeldriver on 2012-11-12
If you've rebooted in the meantime, you will need to run the remount rw command again before resetting your user password 

```
# mount -o remount,rw /
# passwd *yourusername*
```

---

### Post by jobsaditmate on 2012-11-12
My cat /etc/group result:


```
rtkit:x:122:
saned:x:123:
stephen:x:1000:
sambashare:x:124:stephen
guest-nIYHDf:x:125:
guest-KnqV4J:x:126:
guest-uyIdAS:x:127:
guest-nifOS8:x:128:
guest-pYKmi2:x:129:
guest-g0BySE:x:130:
guest-YAric7:x:131:
guest-cUchhx:x:132:
guest-ReK15g:x:133:
guest-UbWSZi:x:134:
guest-j3kG6u:x:135:
guest-3PgFwp:x:136:
guest-im3vZs:x:137:
guest-PaaMyG:x:138:
guest-7pAi4V:x:139:
guest-QHS6ma:x:140:
guest-ss6wcP:x:141:
guest-6TuNOR:x:142:
guest-UI8mTK:x:143:

```

---

### Post by jobsaditmate on 2012-11-12
steeldriver

it worked I successfully changed the password using as you said.  rebooted swithed to the admin log in put in the new password it worked started to boot up and then ..... stalled and went back to the login password screen.  It does this repeatedly.

The only thing I wasn't sure of going back to my horrible journey into password files and changing the "!"  Was that when i edited it I put ":"    either side of the "*" because It was looking thus ":*" and all the other elements of that type had ":" either side of an "*"

I hope to God that makes sense to you.  We are so nearly there and my Woman is calling time on this business soon.  We have been at it most of the day now.

May I also add that I am as grateful as I am amazed at all your support of me here in what is after all a rather silly error on my part - I will definately make a donation to funds after this war is over

---

### Post by steeldriver on 2012-11-12
OK so the symptoms now sound more like a problem with your X session startup rather than a basic password / authentication issue

Can you see if you can log in OK at one of the non-GUI virtual terminals? Ctrl-Alt-F1 etc.

If that works then let's check the ownership / permissions on your home dir and associated files

```
$ ls -ld $HOME

$ ls -l $HOME/.{ICE,X}authority
```

---

### Post by jobsaditmate on 2012-11-12
got into this terminal ok but is there a way to exit it without rebooting (ctrl alt delete)?

code hasn't worked yet but I think I have spaces incorrect

---

### Post by steeldriver on 2012-11-12
you should be able to switch back to the GUI session with Ctrl-Alt-F7 - you can type 'exit' in the F1 virtual terminal to log out of that first if you want but it's not compulsory

---

### Post by jobsaditmate on 2012-11-12
ok answer to the first code Steel:

dr-x------4 username username 4096 june 6 15:37/home/username 

Still don't seem to be getting the format right for your second code

---

### Post by jobsaditmate on 2012-11-12
Going to have to take a break now.  Thank you all so very much for your help.  I will get back at it tomorrow but may (as this is becoming something of an obsession now) look in again for messages / ideas later on tonight

Jobs

---

### Post by steeldriver on 2012-11-12
OK no problem

> **jobsaditmate said:**
> dr-x------4 username username 4096 june 6 15:37/home/username 

You don't appear to have write permission to your own home directory - this is for sure going to prevent your X session from starting so let's try to fix that and see how far we get

---

### Post by philinux on 2012-11-12
> **steeldriver said:**
> OK no problem



You don't appear to have write permission to your own home directory - this is for sure going to prevent your X session from starting so let's try to fix that and see how far we get

I hope the OP is not logged into the guest session to get that output.

---

### Post by JKyleOKC on 2012-11-12
I was away for a few hours. That /etc/group listing of his looked very suspicious; nothing for root or any of the other "system" groups before number 122. That might be normal if taken from the guest account, but I seriously doubt it...

---

### Post by jobsaditmate on 2012-11-12
is there a way of copying text from the terminal so that I can paste back here?

---

### Post by steeldriver on 2012-11-12
> **JKyleOKC said:**
> I was away for a few hours. **That /etc/group listing of his looked very suspicious**; nothing for root or any of the other "system" groups before number 122. That might be normal if taken from the guest account, but I seriously doubt it...

oops - missed that, yes I agree - never seen anything like that before

---

### Post by jobsaditmate on 2012-11-12
I have just created a second admin account for myself, which booted up successfully.  Is it a good idea to delete and bin the original, presumably corrupted, one?

Obviously I would like to salvage file first, if I can, which are basically photographic ones; but it would mean that the OS is saved and this route will negate the need to untangle the code problem?

---

### Post by JKyleOKC on 2012-11-12
> **jobsaditmate said:**
> is there a way of copying text from the terminal so that I can paste back here?I'm using Xubuntu so this might not work for you. I highlight the text, then right-click to get a pop-up menu that includes the "copy" option. I then go to the message reply editor, position the mouse pointer, right-click again, and choose "paste." However I do this when working with a terminal window and a separate browser window; I don't know if it would work if you are using one of the alternate consoles (Ctrl-Alt-F1, etc.).

As for your question about creating another user, my recommendation would be to try to fix the existing problem without throwing anything else into the situation. The less change we make, the less complication we add to the problem.

At this point I think the most important thing to tackle is the lack of write permission to your home directory. I gather from your post that your user name is stephen; can you log into the recovery option again, from grub, and get the root prompt, then use the command "ls -l /home/*" to get a detailed listing of everything under the /home directory and post it here between (code] and (/code] tags (those open parentheses should be open-square-brackets but I don't know how to make them show up correctly)? The main thing I'm looking for with this suggestion is the listing for /home/stephen but also interested in any other directories under /home, and the critical configuration files in your home directory that begin with "." which makes them hidden...

The reason for doing this as root rather than via a normal login is to be sure that we see as much as possible of what's there, regardless of ownership or permissions.

It's getting late here so I may be gone for the next 8 to 10 hours or so...

---

### Post by jobsaditmate on 2012-11-13
Got back in there and I think I have the data JKyle requested but I return to my earlier question of how I go about copying it and bringing to firefox?  Currently I reboot to get here.  Also in the GRUB terminal I cannot move the page up or down and the mouse track pad etc are inoperative.

Sorry to be a dunce but all I know is what you good people have told me and I do hesitate in using my initiative down there in the bowels of me laptop.

---

### Post by JKyleOKC on 2012-11-13
I'm back again, and now I think I understand why your listing of /etc/group omits all the groups numbered below 122. When you go to the root prompt or in your words "the GRUB terminal" you are not in a terminal window, but in an actual terminal so when something scrolls off the top of the screen you cannot copy it to post here!

Since the forum software here is totally oriented toward GUI use, this is a real problem from both your end and ours; unfortunately at this point I don't know how to solve it. It's possible to save the result of a command to a text file instead of displaying it on the screen, but I don't know the way (if there is one) to get that file into a message reply here, from the root prompt.

Phil, steeldriver, do you have any ideas to get past this?

Jobsaditmate, I don't think the situation is hopeless or needing much more to get things back on track for you, but until someone jumps in with ideas for getting some diagnostic information posted to show us details I'm a bit lost...

Can you boot from the Live CD or USB just as you did when installing the system, and choose the "try Ubuntu" option when it starts? If so, then I think we may have the way to move forward using that. Before I go into all the detail of doing so, though, we need to know if it still works for you...

---

### Post by steeldriver on 2012-11-13
could try pastebin maybe? then just need to copy the url number

```
# apt-get install pastebinit
```

Then just

```
# cat /etc/group | pastebinit
```

or whatever - see [https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

(instructions are old but I just checked it works on my 12.04 box)

---

### Post by jobsaditmate on 2012-11-13
ok, tried to install pastebinit and it started the process and stopped to ask if ok to use memory Y/n when I answered Y it came back with :

```
Err http://gb.archive ubuntu.com/ubuntu/precise-updates/uniververse pastebinit all 1.3 ubuntu 2.1 could not resolve 'gb.archive.ubuntu.com ...
```

It went on but hopefully there is enough there?

---

### Post by steeldriver on 2012-11-13
Are you still in the recovery console or did you manage to log in with your regular (admin) user at the Ctrl-Alt-Fn virtual terminal? 

If you're in the recovery console the error is probably because networking is not configured when you are there - if so try again booting normally and then logging in at the virtual terminal instead if possible (you will need sudo from there of course)

```
$ sudo apt-get install pastebinit
```

---

### Post by jobsaditmate on 2012-11-13
pastebinit installed successfully now but when I put in ```
cat /etc/group | pastebinit
``` it just kind of hangs up with a flashing "-" symbol?

---

### Post by steeldriver on 2012-11-13
Hmm, well it should return a URL, something like

```
$ cat /etc/group | pastebinit
http://paste.ubuntu.com/1356947/
```Maybe networking still isn't available so it can't write the remote file? Let's not get too hung up on that though - am I right that your issue now is that you can't start a GUI session with your original admin account? and we found out last night that the account permissions are wrong? can you please re-run

```
$ ls -ld ~
```(that's a tilde character or 'twiddle' - shorthand for 'current user's home directory' - but you can use the longhand 'ls -ld /home/yourusername' if you prefer) from the virtual terminal where you are now - you should see something like

```
$ ls -ld ~
drwxr-xr-x 2 steeldriver steeldriver 4096 Nov 13 20:03 /home/steeldriver
```

The bit we're most interested in is the 'drwxr-xr-x'

---

### Post by jobsaditmate on 2012-11-14
```
dr-X------4 stephen stephen 4096 june 6 15:37 /home/stephen
```

---

### Post by steeldriver on 2012-11-14
OK let's try to fix that

At a minimum I think you need write permission for your home directory - else X can't write the .Xauthority or .xsession-errors files and so on

```
chmod u+w /home/stephen
```and let's start with new authority files just in case

```

rm /home/stephen/.Xauthority
rm /home/stephen/.ICEauthority

```I *believe* that the standard permissions for 12.04 desktop (with user  private groups - umask = 0002) are -rw-rw-r-- for regular files and drwxrwxr-x for  dirs so; we could do a recursive chmod at this point - but let's see how far we get before jumping in and changing too much.

---

### Post by jobsaditmate on 2012-11-14
Sorry for delay Steel.  Busy day

first one went in and simply returned to #prompt without comment

second two failed to recognise the X or ICE files as existing?

---

### Post by steeldriver on 2012-11-14
OK that's not necessarily a problem - what happens now if you reboot normally (i.e. not into the recovery console)?

---

### Post by jobsaditmate on 2012-11-14
Sorry that was ctrl alt F1 ... the $ prompt?

---

### Post by westie457 on 2012-11-14
@ steeldriver

Is it possible to add a user account as administrator via the command line?
If it is possible the new account could be used to unlock the disabled account. As I have no idea how to do this it is only a suggestion that might work.

---

### Post by steeldriver on 2012-11-14
yes absolutely should be possible - either from the recovery console

```
# gpasswd --add *newuser* sudo
```or from the virtual terminal logged in as the existing admin user

```
$ sudo gpasswd --add *newuser* sudo
```

---

### Post by jobsaditmate on 2012-11-14
I have admin account up and running added via the normal route?  New password work to authenticate for the original admin account.  It's just now that the old account wont boot up properly - it stalls and returns to login screen

---

### Post by steeldriver on 2012-11-14
Have you tried graphical login to the old account (stephen) since you gave its home directory write permission?

---

### Post by jobsaditmate on 2012-11-14
It works!  I'm in to the original admin account.  Though all the files are gone

---

### Post by jobsaditmate on 2012-11-14
by file I mean photos, videos, music docs etc

---

### Post by jobsaditmate on 2012-11-14
bedtime!  I'll look in again in the morning though..  Thanks to all.

---

