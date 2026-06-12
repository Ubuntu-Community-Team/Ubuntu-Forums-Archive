---
title: "can you rmind me how to solve the problem of the app store not getting updated?"
date: 2024-09-20
forum: General Help
---

### Post by ronjjjg8885 on 2024-09-20
hello
i've trying to update it. but i get the message that i attached below..
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294262&stc=1[/IMG]
i've already tried to reboot. but it is in the same state..

BTW
i'm not an advanced user........


tnx
and love from israel!!!!!!

---

### Post by Holger_Gehrke on 2024-09-20
The problem is that the Appstore can't update programs that are currently running and that of course means it can't update itself. So you need to close it. This only removes the window, the program stays running. So next you need to actually stop it, which should be done from the command line with 'pkill snap-store'. So now you can tell snap to refresh the snap-store package with the command 'snap refresh snap-store'.

Holger

---

### Post by ronjjjg8885 on 2024-09-20
done. thank you!!
but why it does not closes itself?
why do i need to kill and then update it?

it is very confusing for those who want up to date software but are not familiar with that.........

---

### Post by Holger_Gehrke on 2024-09-21
The snap store is based on gnome-software which behaves the same. The idea here is that gnome software takes a long time to start up since it always checks all the sources of software for any updates or new entries. By staying active in the background it can keep on doing these updates in the background so that it opens instantly when you start it again (basically if you start the program again it checks whether there's already an instance of it running and if so tells that instance to show itself and then quits).

Holger

---

### Post by ronjjjg8885 on 2024-09-21
isn't it possible to change it so it will act similar to the google play store that can update itself in the background?....

---

### Post by 1fallen on 2024-09-21
This is not for everyone,                                []("https://askubuntu.com/posts/1504046/timeline")  
          
                       To avoid the issue above and other related snap-store [bugs]("https://askubuntu.com/questions/1469200/how-can-i-dismiss-software-updates-installed-notification/") and [failings]("https://forum.snapcraft.io/t/pending-update-of-snap-store-but-no-update-available/34415").
I removed snap-store:
```
snap remove snap-store
```
But I don't need a GUI Software Center either, but you can  still use gnome-software which manages snaps perfectly without any of the above  issues. gnome-software also has the advantage that it handles flatpak  and DEB packages.

**NOT FOR EVERYONE!

---

### Post by ronjjjg8885 on 2024-09-23
i see
my question was more intended to ask why it is not fixed somehow? i mean why not to make the 'snap store' to be updated by itself without any problem..

if you don't have an answer for that never mind..

btw....
if i remove the snap store the software updater will automatically take charge on the software from the snap store that need updating?

---

### Post by 1fallen on 2024-09-23
> **ronjjjg8885 said:**
> i see
my question was more intended to ask why it is not fixed somehow? i mean why not to make the 'snap store' to be updated by itself without any problem..

if you don't have an answer for that never mind..
I'm sure you understood that from my thread, if not, no it dose not address your question, but as a workaround for the Bugs or needed features, and less frustration for the user.
> **ronjjjg8885 said:**
> 
btw....
if i remove the snap store the software updater will automatically take charge on the software from the snap store that need updating?

Yes, and your "not" locked out of reinstalling snap-store

---

### Post by grahammechanical on 2024-09-23
Ubuntu has three ways to update software. 1) the Software Updater utility. 2) the terminal - command line. 3) the software centre or app store.

The Software Updater utility checks for updates when we launch it. The software centre checks for updates when we login to the desktop. If we try to use the command line to update while software centre is checking for updates we will get an error message. We have to wait.

As far as I can tell the software centre as a snap package automatically updates itself once the initial update check is completed. The same thing happens with other snap packaged apps such as Firefox, Thunderbird and zoom workplace in my experience.

Regards

---

### Post by donald187 on 2024-09-23
> **ronjjjg8885 said:**
> i see
my question was more intended to ask why it is not fixed somehow? i mean why not to make the 'snap store' to be updated by itself without any problem..

if you don't have an answer for that never mind..


I happened to stumble across this.  Check out d-loose's comment in the following GitHub thread.

> 
First of all - the app center cannot update itself, because it simply  tells snapd to do the update, which it can't do because the app center  is running. We should try to come up with a solution for this  eventually, though.


[https://github.com/ubuntu/app-center/issues/1391](https://github.com/ubuntu/app-center/issues/1391)

---

### Post by ronjjjg8885 on 2024-09-24
>  	 		 			 			 				First of all - the app center cannot update itself, because it  simply  tells snapd to do the update, which it can't do because the app  center  is running. We should try to come up with a solution for this   eventually, though. 			 		

 	
 


tnx all
can you explain in a simplified way how could a future might solution work that it can't be done at present?

---

### Post by donald187 on 2024-09-24
> **ronjjjg8885 said:**
> tnx all
can you explain in a simplified way how could a future might solution work that it can't be done at present?

I can't.  Perhaps someone else can.

---

### Post by ronjjjg8885 on 2024-10-09
so if i remove the snap store all the apps will get updated with the software updater? if yes, are you sure about it?

---

### Post by nicolasdentremont on 2024-10-09
> **ronjjjg8885 said:**
> so if i remove the snap store all the apps will get updated with the software updater? if yes, are you sure about it?

I don't have the snap store but I still have some snap applications. I update them with:
```
snap refresh
```

---

### Post by ronjjjg8885 on 2024-10-10
can i make the software updater to update snap easily?
i don't want to type commands
i think it is not a good idea to split the updates to two separate apps [app center and software updater]

---

### Post by Holger_Gehrke on 2024-10-11
snaps will always update automatically thanks to snapd looking for updates automatically four times per day unless you configure it to not do so or do something different. If snap-store isn't running it will get updated that way, too. So the easiest way to keep your system up to date is to let the Updater take care of the Debian packages and let snapd - which will be running anyway if you're using snaps - do it's thing for snaps.

Holger

---

### Post by ronjjjg8885 on 2024-10-12
ok
tnx

---

