---
title: "login fails after doing partial upgrade"
date: 2015-05-04
forum: General Help
---

### Post by rawlins02 on 2015-05-04
Running 14.04. A few days ago I received a message saying there were broken packages, and suggesting I do a partial upgrade. Partial upgrade seemed to work OK. Yesterday I shut down the system. Now my password will not work at login. Message says "Failed to start session".  I understand this has happened with other users. Just would like suggestions before attempting to fix.

Edit:  Dropping from GUI to command line using Ctrl-Alt-F1, I am able to login. So account and password are intact.

---

### Post by dino99 on 2015-05-04
Always avoid partial upgrade (but now you already know why)
Try booting into recovery-mode, activate the network, then select the command line, and update then try fixing the broken package. Maybe that broken can be purged then reinstalled, if not, then try reconfiguring it.

---

### Post by rawlins02 on 2015-05-04
Specific commands to do this?  I'm fairly comfortable with these things, and refer to do repair in a way which has worked for others. This appears to be a different approach:

[http://itsfoss.com/failed-to-start-session-ubuntu-14-04/](http://itsfoss.com/failed-to-start-session-ubuntu-14-04/)

---

### Post by Bashing-om on 2015-05-04
rawlins02; Hello;

In a situation such as this where the system is intact and you can login from terminal, but not able to activate the GUI; I always suspect a loss of authorization to access the GUI.

What returns from terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Where they should be owned and grouped by "you" .

Else; well we poke at it some place else.

[INDENT][INDENT]maybe,
[INDENT][INDENT][INDENT]just a little thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
[QUOTE=Bashing-om;13278549]rawlins02; Hello;

In a situation such as this where the system is intact and you can login from terminal, but not able to activate the GUI; I always suspect a loss of authorization to access the GUI.

What returns from terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home

```
Where they should be owned and grouped by "you" .


```

ls -al .Xauthority
-rw------- 1 rawlins rawlins 158 May  4 08:41 .Xauthority

ls -al .ICEauthority
-rw------- 1 rawlins rawlins 103269 May  4 08:41 .ICEauthority

ls -al /home
drw------- 1 rawlins rawlins 103269 May  2 16:28 rawlins/


```

This seems right. Perhaps the solution is as described in the link I listed in post #3 ?

---

### Post by Bashing-om on 2015-05-04
rawlins02; Yeah;

agreed. does not look to be an authorization issue.


Wont hurt to poke and see what bites back:
Rather than the more intrusive shotgun approach as advised from the link in post #3, may I suggest:
```

sudo dpkg-reconfigure lightdm
update-desktop-database

```

See if there are any error conditions reported .

Fault isolation;
[INDENT][INDENT]look'n for that where
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
I'm assuming unmet dependencies are source of problem.

```

> sudo apt-get install  ubuntu-desktop

```
The following packages have unmet dependencies
ubuntu-session
unity-control-center
unity-settings-daemon

How does one resolve this?

---

### Post by Bashing-om on 2015-05-04
rawlins02; Surprising ;

Is this not a standard desktop install of 14.04 ? As those dependencies should be present .

Let's get a status:
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]light begins to dawn
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
> **Bashing-om said:**
> rawlins02; Yeah;

agreed. does not look to be an authorization issue.


Wont hurt to poke and see what bites back:
Rather than the more intrusive shotgun approach as advised from the link in post #3, may I suggest:
```

sudo dpkg-reconfigure lightdm
update-desktop-database

```

See if there are any error conditions reported .

Fault isolation;
[INDENT][INDENT]look'n for that where
[/INDENT][/INDENT]


```

sudo dpkg-reconfigure lightdm
update-desktop-database

The databases in [/usr/local/share/applications, /usr/share/applications] could not be updated


```

I should mention that I'm typing all of this out into a web browser on another computer, so I am limited in what information from the disabled machine I can post.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Plot thickens;

Is this a standard DeskTop install that we are working on ?

Do these directories even exist on the system?
```

ls -al /usr/local/share/applications
ls -al /usr/share/applications

```

[INDENT][INDENT]what to do, OH waht to do
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
Yes standard desktop install.

There is no /usr/local/share/applications

There is a /usr/share/applications

which contains many files *.desktop

---

### Post by Bashing-om on 2015-05-04
rawlins02; Hummm ...

I am experiencing a failure to understand. The error "  The databases in [/usr/local/share/applications, /usr/share/applications] could not be updated " when the database file does exist . Hummm

Does "root" own every thing from the top of the file system hierarchy all the way inclusive of the files contained in "/usr/share/applications" directory ? ( grasping at straws) 

How much of this relates to the desktop not starting ? Unknown at this time.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
Yes root is owner on all directories on down to /usr/share/applications

I believe there are broken packages being held. But every attempt at identifying or fixing has been unsuccessful.

I just tried installing the unmet dependecies via aptitude

```

> sudo aptitude install ubuntu-session
> sudo aptitude install unity-control-center
> sudo aptitude install unity-settings-daemon

```

This did not return errors, but I'm not sure anything was installed.

And now I have run out of battery, so must wait a few hours to resume.  Matter unsolved.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Well ...

I do have another thought in mind.
1st though, backup to making sure the package manager is stable and seeing what it screams and hollers about.
Does
```

sudo apt-get update
sudo apt-get upgrade

```
run clean ?
Depending, then we proceed .

[INDENT]poke at it
[INDENT][INDENT][INDENT]'til something gives
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
Yes, both ran clean. The update listed many "Hit" and "Get" and listed several repositories. Ended with "Done" and no error. The upgrade ran with zero upgraded, installed, to be removed, and zero not upgraded.

---

### Post by Bashing-om on 2015-05-04
rawlins02; OK ;

Let's try this - one more step up the ladder:
```

sudo service lightdm stop
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

[INDENT][INDENT]maybe now
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
The commands:

```

sudo dpkg-reconfigure lightdm
update-desktop-database

```

now runs without error. Attempting to install ubuntu-desktop

```

> sudo apt-get install  ubuntu-desktop

```

still gives error due to unresolved dependencies, exactly as described here:
[http://askubuntu.com/questions/505049/ubuntu-14-04-you-have-held-broken-packages](http://askubuntu.com/questions/505049/ubuntu-14-04-you-have-held-broken-packages)

Unless I'm mistaken there was no solution posted on that page.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Humm ..

Reference the askubuntu link, I see no conflicting Desktop Environments at play here; But if "held broken packages" is an issue:
What results:
```

dpkg --get-selections | grep hold

```
should tell us.

[INDENT][INDENT]gotta be something small I am overlooking
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
> **Bashing-om said:**
> rawlins02; OK ;

Let's try this - one more step up the ladder:
```

sudo service lightdm stop
sudo dpkg-reconfigure lightdm 
sudo dpkg-reconfigure unity-greeter 
sudo service lightdm start

```

[INDENT][INDENT]maybe now
[/INDENT][/INDENT]


Loged in as root, those commands ran without error. The lightdm start kicked the system back to the login screen. Entering password for user rawlins still fails to allow login. Would restting password fix this, or is unity buggered up?

---

### Post by Bashing-om on 2015-05-04
rawlins02; Again

Back to checking we have not lost access to the GUI
> 
Loged in as root

As looping back to the log in screen is the prime symptom :
```

ls -al .Xauthority
ls -al .ICEauthority

```

Now I await and make sure all is caught up - cross posting - 
see then where we stand.

[INDENT][INDENT]it's them little things
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
> **Bashing-om said:**
> rawlins02; Again

Back to checking we have not lost access to the GUI

As looping back to the log in screen is the prime symptom :
```

ls -al .Xauthority
ls -al .ICEauthority

```

Now I await and make sure all is caught up - cross posting - 
see then where we stand.

[INDENT][INDENT]it's them little things
[/INDENT][/INDENT]

I should make clear that I am having issues logging in (at login screen GUI) as user rawlins. I'm doing all of the system apt-get and dpkg commands as root. 

I'm not sure I understand the access to GUI issue you mention.

Using ctrl-alt-F1 to log in as rawlins, the file, .Xauthority in that account has permissions read+write for owner, readable to group and others. .ICEauthority has permissions read+write for owner. No desgnations for group and others.

```

dpkg --get-selections | grep hold

```

ran without error or anything produced at standard output.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Well,

Just trying to help and find the solution in a systematic method. With no particular errors reported makes it tough.

As re-configuring doesn't help and it is not a permission issue ; how 'bout removing any saved user-sessions:
```

rm ~/.dmrc 

```
Reboot - just to make sure memory is cleared - and now what results ?

[INDENT][INDENT]still, something simple - I think
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
I did the rm .dmrc. Shut down computer. Started and attempted my login as user rawlins. Still get "Failed to start session".  I'm failing behind on work and may resort to using a second computer for next couple days. I regret to say a fresh install of OS may be easier. Very aprehensive of 14.04 and it's desktop system.

---

### Post by wildmanne39 on 2015-05-04
I have been using 14.04 desktop without trouble for several months, so there is not an issue with 14.04.

A partial upgrade is always bad and break things, you sure do not want to ever do one.

If time is a factor then I you might should reinstall, but there is almost always a way to fix it.

You can try this real quick if it does not work then I would do what you need to for your work.

Use <ctrl><alt><f1> to switch to text mode. Log in and do: ```
rm .{X,ICE}authority
```
The command courtesy of Krytarik because I just could  not find it in my files.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Yeah ..

A (re-)install might be the faster more expedient thing to do . But we learn nothing taking that solution.
With no errors reported, we still do not know what the root cause is .
All I know to do is to try "something" looking for errors that might be generated.

Presently I do not know how to proceed. I will consider and see what comes to mind.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by rawlins02 on 2015-05-04
Thanks for your help. Problem solved. As suggested here:

[http://askubuntu.com/questions/505049/ubuntu-14-04-you-have-held-broken-packages](http://askubuntu.com/questions/505049/ubuntu-14-04-you-have-held-broken-packages)
and here:
[http://askubuntu.com/questions/537263/reinstall-ubuntu-desktop-after-removing-gnome](http://askubuntu.com/questions/537263/reinstall-ubuntu-desktop-after-removing-gnome)

Installation of gnome-settings-daemon-schemas=3.8.6.1-0ubuntu11.2  allowed subsequent installation of ubuntu-desktop, and login to the account. I'll leave it to others to determine if and how there is an issue with dependencies etc. I've yet to determine if there are any broken packages at this time. Thanks again for the suggestions. It appears there are several of us now that have experienced a similar issue.

---

### Post by Bashing-om on 2015-05-04
rawlins02; Great !

Sweat condition 3 terminated.
Thanks for pointing to the solution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

