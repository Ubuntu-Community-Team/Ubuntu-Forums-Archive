---
title: "audio recorder won't write to file"
date: 2021-01-31
forum: General Help
---

### Post by Old Jimma on 2021-01-31
Hi Community:

I am using audio recorder.

when I click "Start Recording" it gives me a messages "Cannot writ to file /home/itchy/xxx/yyy.ogg"

I know that I have read/write/execute privilege in the  /home/itchy/xxx directory and everything in it... files and directories.

How do I get audio recorder to record and write the the directory/file I specify?

Sad Old Jimma

---

### Post by Yellow Pasque on 2021-01-31
It's not the snap version of audio recorder, is it?

---

### Post by Old Jimma on 2021-01-31
I do not know: I can't remember. How would I find out?

---

### Post by Old Jimma on 2021-01-31
I do not think it was a snap. I got advice on how to install it on the forums here: [https://ubuntuforums.org/showthread.php?t=2456380&p=14013913#post14013913]("https://ubuntuforums.org/showthread.php?t=2456380&p=14013913#post14013913")

it was a .deb file

Old JImma

---

### Post by HermanAB on 2021-01-31
Try running the audio recorder from the command line, then look at the error messages.  You will see more useful errors this way.

---

### Post by ajgreeny on 2021-01-31
Just to double check that it's not a snap version run command ```
snap list
``` and see what you do have.
It is possible to have both versions installed and be unaware of that fact.

---

### Post by CelticWarrior on 2021-01-31
> **ajgreeny said:**
> Just to double check that it's not a snap version run command ```
snap list
``` and see what you do have.
It is possible to have both versions installed and be unaware of that fact.

Sure.. But snap or not isn't the problem here. Not everything about permissions is snap related!
Snaps can always write to the userspace.

```
[COLOR=#000000]Cannot write to file /home/itchy/xxx/yyy.ogg[/COLOR]
```
therefore cannot be related with a snap. And it isn't a snap anyway: [https://ubuntuforums.org/showthread.php?t=2456380&p=14013913#post14013913](https://ubuntuforums.org/showthread.php?t=2456380&p=14013913#post14013913)

[B]The problem is with the permissions of the "xxx" folder and/or the "yyy" file.
[/B]

---

### Post by Old Jimma on 2021-01-31
I am pretty sure that the permissions are correct. I used:

sudo chmod -R 777 /home/itchy/xxx

An ls -lisa showed I had read write and execute privileges.

This is not the first time I've had the problem with audio recorder.

What I'm doing is simple: trying to write in a directory that is nested beneath my home directory. by default, I've got privileges there.

I think something is going on with audio-recorder. 

OLD JIMMA

---

### Post by HermanAB on 2021-02-01
Laak Ah sed: Run it from the command line.  You will then get more meaningful error messages.

---

### Post by ajgreeny on 2021-02-01
I think you should quickly change your permissions for that /home/itchy/xxx back to a more secure level.

Giving any folder 777 permissions gives anybody full access to do whatever they decide with the contents, and is something that should be avoided at all times, other than perhaps temporarily changing them to 777 to test whether or not permissions are stopping something occurring that you need.

---

### Post by HermanAB on 2021-02-02
Note that there is more to file permissions that chmod and chown.  There are also ACLs, AppArmor and SELinux, any one of which can cause you grief.

---

