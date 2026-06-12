---
title: "you do not have permission to remove this software"
date: 2021-03-01
forum: General Help
---

### Post by robertsaron on 2021-03-01
I am on ubuntu 20.04 and get an error when installing or removing software:  you do not have permission to remove this software or you do not have permission to install this software. This is the error I get when trying to install/remove software in the ubuntu software center.

---

### Post by TheFu on 2021-03-02
Installing and removing software system-wide is an admin task, so admin privileges are required.
On Ubuntu systems, there are a few ways to elevate the current permission level. The most common method is to use **sudo**.

Only selected userids are allowed to use the sudo program.  You can check that by running the '**id**' command in any terminal on the machine.  If the userid is not a member of the *sudo* group, then it will not be possible.

It appears you've been here a long time, so perhaps the question just needs more clarity? By now you are probably used to using sudo. Yes?

---

### Post by ActionParsnip on 2021-03-02
What is the output of:
```

sudo apt update
sudo apt upgrade

```
Thanks

---

### Post by robertsaron on 2021-03-02
I have the admin credentials for the system. The ubuntu software center normally prompts for the admin password. But for some reason it stopped doing that. I was on 20.04 LTS, and then upgraded to 20.10, and still the same problem. Now I do not even get the error message, I just see the progress bar, start, and it goes back to the install screen. I can install stuff just fine from the terminal.

I have been all over the internet and It appears this was a common problem, with earlier versions or with the polkit files, whatever those do. I did modify a file in the polkit folder, to get the messages about color profiles to go away, when I remote into the computer. I also have ubuntu LTS 20.04 on my laptop, and I have not messed with the install hardly at all. And it gives the same error message, as my desktop.

Sudo apt-get upgrade output:[I] Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
[/I]

sudo apt-get upgrade output: [I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

---

### Post by robertsaron on 2021-03-04
So I figured out the problem. When I remote into my Ubuntu Desktops,  a message pops up with the following dialog box: Authencation is required to create a color profile. How ever entering in a username and password or hitting cancel, does not dismiss this dialog box. In creating a file, in the following folder: *etc/polkit-1/localauthority.conf.d/*

The file is called: *2-allow-colord.conf*

The following is then entered into the file:
*polkit.addRule(function(action, subject) { if ((action.id == "org.freedesktop.color-manager.create-device" || action.id == "org.freedesktop.color-manager.create-profile" || action.id == "org.freedesktop.color-manager.delete-device" || action.id == "org.freedesktop.color-manager.delete-profile" || action.id == "org.freedesktop.color-manager.modify-device" || action.id == "org.freedesktop.color-manager.modify-profile") && subject.isInGroup("{users}")) { return polkit.Result.YES; } });*

In looking all over the internet, when people remote into their Ubuntu desktops, for gnome, the notification about the profile pops up, and cannot be dismissed. How ever in creating the file do permanently do away the color profile notifcation, this prevents the installation and removal of software through the software center. 

Is there anyway to get that annoying message to go away about the color profile, without putting that file in the polki-1 folder? 

I use chrome remote desktop, and in my research, have seen that no matter what RDP program is used, this color profile message comes up. Any ideas?

---

### Post by TheFu on 2021-03-04
Don't use rdp. Use **ssh -X**.  A full desktop isn't very efficient.

---

### Post by robertsaron on 2021-03-04
Well I FINALLY found a fix, and I have no idea what it was. I can find it again, possibly, if anyone wants to know.

---

### Post by kbramesh on 2022-02-12
Can you please tell me what worked? I am having this same issue. I tried the same fix to the polkit issue and now I have the same problem

---

### Post by MAFoElffen on 2022-02-12
> **robertsaron said:**
> Well I FINALLY found a fix, and I have no idea what it was. I can find it again, possibly, if anyone wants to know.
Yes, it would be useful to know what caused that and what fixed it... I'm curious about this.

---

### Post by #&amp;thj^% on 2022-02-12
> **MAFoElffen said:**
> Yes, it would be useful to know what caused that and what fixed it... I'm curious about this.

Will you check this one out Please; [https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile](https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile)
Post by Nemo
Unless your unaffected of couse. :)
> **MAFoElffen said:**
> Yes, it would be useful to know what caused that and what fixed it... I'm curious about this.
I know you know but for others:
The Culprit: Polkit
Ubuntu uses a software component called Polkit, which is an application authorization framework that captures actions performed by a user to check if the user is authorized to perform certain actions.
When you connect to Ubuntu remotely using  lets say RDP / Windows Remote Desktop, you will see the above errors because the Polkit Policy file cannot be accessed without superuser authentication.

---

### Post by #&amp;thj^% on 2022-02-12
> **robertsaron said:**
> 

Is there anyway to get that annoying message to go away about the color profile, without putting that file in the polki-1 folder? 

I use chrome remote desktop, and in my research, have seen that no matter what RDP program is used, this color profile message comes up. Any ideas?
I'm not sure of security implications here, and your issue is solved, a while ago on one of my severs I had to change:
```
# cd /usr/share/polkit-1/actions/

# vi org.freedesktop.color.policy   ### nano works here as well
```

Modify <allow_any> settings from auth_admin to yes.

```
<defaults>
      **<allow_any>yes</allow_any>**
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
```
and reboot. no warranty implied >>> but it stoped that annoying window. :p
[/CODE]

---

### Post by MAFoElffen on 2022-02-13
> **1fallen said:**
> Will you check this one out Please; [https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile](https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile)
Post by Nemo
Unless your unaffected of couse. :)

I know you know but for others:
The Culprit: Polkit
Ubuntu uses a software component called Polkit, which is an application authorization framework that captures actions performed by a user to check if the user is authorized to perform certain actions.
When you connect to Ubuntu remotely using  lets say RDP / Windows Remote Desktop, you will see the above errors because the Polkit Policy file cannot be accessed without superuser authentication.
I checked this out and tested this for myself. I could recreate the problem and work through it...

It is sort of a hybrid problem where the link 1fallen posted a link solution(s), sort of... It's a but more complex The explanations there are a bit lacking, but the answers are there. Explained- Well the real solution is actually spread over two different answers there, deoending on whatversion of Ubuntu you are running and the version of polkit. I know I probably lost a few with that, so let me explain. Yes polkit is the culprit.

I first create the file "/etc/polkit-1/localauthority.d.conf/02-allow-color.d.conf" with the contents:

```

polkit.addRule(function(action, subject) {
if ((action.id == &#8220;org.freedesktop.color-manager.create-device&#8221; ||
action.id == &#8220;org.freedesktop.color-manager.create-profile&#8221; ||
action.id == &#8220;org.freedesktop.color-manager.delete-device&#8221; ||
action.id == &#8220;org.freedesktop.color-manager.delete-profile&#8221; ||
action.id == &#8220;org.freedesktop.color-manager.modify-device&#8221; ||
action.id == &#8220;org.freedesktop.color-manager.modify-profile&#8221;) &&
subject.isInGroup(&#8220;{users}&#8221;)) {
return polkit.Result.YES;
}
});

```
With this file in place, during a remote connection, if a user is a part of the group 'users', they will be allowed to perform colord actions defined in the policy file. No more popus will show up saying that their is an authentication problem, BUT-- It will start popping up other kinds of apport popups saying there was a system crash caused by a problem with /usr/sbin/xdrp-chsrv crashing... 

That is the crash information details I got in apport... While I was trying to connection from a remote PC using rdp as the connection... So this accepted solution, although it got rid of the authorization problem, causes a system crash... 

It seems that if the version of polkit is 0.106 and newer, the above file is the solution, a file ending with the extension of .conf and in that format. But less than that version needs a different file format, with an extnsion of .pkla.Ubuntu 20.04.3 uses polkit version 0.105...

The working solution for Ubuntu 20.04.3 was:
In the voted answ er (#32) there, it has you create a file /etc/polkit-1/localauthority/50-local.d/45-allow-colord.pkla with this contents:
```

[Allow Colord all Users]
Identity=unix-user:*
Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.freedesktop.color-manager.modify-profile
ResultAny=no
ResultInactive=no
ResultActive=yes

```
Which says any user has the right to use colord... But that wasn't the full answer either...

The rest of the story is that there are other things you need to do also... You need to empty the crash directory before you retry any connection again after that first...
```

sudo rm /var/crash/*

```
And then you need to reload xrdp for all of it to take affect, prior to trying to connect... (Actually, both of those didn't really seem to take affect until xrdp was reloaded).
```

sudo systemctl restart xrdp

```
Then it connected without any errors or crashes...

Remember that with RDP, there is a caveat, immaterial if the target PC  is Linux or Windows... You cannot log in with RDP with a UserID that is  already logged in. That user needs to be logged out to connect.  Sometimes, depending on the client, you will either have a black screen,  or get a connection refused dialog. Some admin's will create a RP user  just for that kind of connection so it has a higher change of success.  At least that was one of those "best practice" kinds of things I was  taught. Also what we used to do, after getting it working, was to tunnel the RDP connections within SSH or VPN tunnels...

---

### Post by #&amp;thj^% on 2022-02-14
> **MAFoElffen said:**
> I checked this out and tested this for myself. I could recreate the problem and work through it...

It is sort of a hybrid problem where the link 1fallen posted a link solution(s), sort of... It's a but more complex The explanations there are a bit lacking, but the answers are there. Explained- Well the real solution is actually spread over two different answers there, deoending on whatversion of Ubuntu you are running and the version of polkit. I know I probably lost a few with that, so let me explain. Yes polkit is the culprit.

I first create the file "/etc/polkit-1/localauthority.d.conf/02-allow-color.d.conf" with the contents:

```

polkit.addRule(function(action, subject) {
if ((action.id == “org.freedesktop.color-manager.create-device” ||
action.id == “org.freedesktop.color-manager.create-profile” ||
action.id == “org.freedesktop.color-manager.delete-device” ||
action.id == “org.freedesktop.color-manager.delete-profile” ||
action.id == “org.freedesktop.color-manager.modify-device” ||
action.id == “org.freedesktop.color-manager.modify-profile”) &&
subject.isInGroup(“{users}”)) {
return polkit.Result.YES;
}
});

```
With this file in place, during a remote connection, if a user is a part of the group 'users', they will be allowed to perform colord actions defined in the policy file. No more popus will show up saying that their is an authentication problem, BUT-- It will start popping up other kinds of apport popups saying there was a system crash caused by a problem with /usr/sbin/xdrp-chsrv crashing... 

That is the crash information details I got in apport... While I was trying to connection from a remote PC using rdp as the connection... So this accepted solution, although it got rid of the authorization problem, causes a system crash... 

It seems that if the version of polkit is 0.106 and newer, the above file is the solution, a file ending with the extension of .conf and in that format. But less than that version needs a different file format, with an extnsion of .pkla.Ubuntu 20.04.3 uses polkit version 0.105...

The working solution for Ubuntu 20.04.3 was:
In the voted answ er (#32) there, it has you create a file /etc/polkit-1/localauthority/50-local.d/45-allow-colord.pkla with this contents:
```

[Allow Colord all Users]
Identity=unix-user:*
Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.freedesktop.color-manager.modify-profile
ResultAny=no
ResultInactive=no
ResultActive=yes

```
Which says any user has the right to use colord... But that wasn't the full answer either...

The rest of the story is that there are other things you need to do also... You need to empty the crash directory before you retry any connection again after that first...
```

sudo rm /var/crash/*

```
And then you need to reload xrdp for all of it to take affect, prior to trying to connect... (Actually, both of those didn't really seem to take affect until xrdp was reloaded).
```

sudo systemctl restart xrdp

```
Then it connected without any errors or crashes...

Remember that with RDP, there is a caveat, immaterial if the target PC  is Linux or Windows... You cannot log in with RDP with a UserID that is  already logged in. That user needs to be logged out to connect.  Sometimes, depending on the client, you will either have a black screen,  or get a connection refused dialog. Some admin's will create a RP user  just for that kind of connection so it has a higher change of success.  At least that was one of those "best practice" kinds of things I was  taught. Also what we used to do, after getting it working, was to tunnel the RDP connections within SSH or VPN tunnels...

Can't tell you how much I appreciate your time and efforts here in UF. ;)
And that's pretty much how I would have laid it out. :)
Moral to the story, there was not just 'one' suggested solution on the link that fit everyone.

In post #11 I took a more unconventional approach, and it got the job done.
Please also read that post it has a important heads-up declared.
I was the only person allowed on that machine mentioned.
Best Regards :)

---

### Post by kbramesh on 2022-02-16
The issue is fixing this issue with the solution outlined in 
[https://unix.stackexchange.com/quest...-color-profile]("https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile")
then results in the problem of not being able to download  anything from the App Store or delete any software because of the "You don't have permissions" error, which disappears when you roll back the solution described above. 

Is there a way to prevent the authentication messages without creating the "Permission" problem?Do the suggestions above fix both?

---

### Post by #&amp;thj^% on 2022-02-16
> **kbramesh said:**
> The issue is fixing this issue with the solution outlined in 
[https://unix.stackexchange.com/quest...-color-profile]("https://unix.stackexchange.com/questions/417906/authentication-is-required-to-create-a-color-profile")
then results in the problem of not being able to download  anything from the App Store or delete any software because of the "You don't have permissions" error, which disappears when you roll back the solution described above. 

Is there a way to prevent the authentication messages without creating the "Permission" problem?Do the suggestions above fix both?

Did you try my suggestion in post #11 I'm curious currently, as my issue was from a year or slightly more ago

---

