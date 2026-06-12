---
title: "Problem connecting to windows shares from command line"
date: 2005-10-31
forum: General Help
---

### Post by berbs on 2005-10-31
I am trying to mount a windows share. It works using "connect to Server..." from the places menu but does not work from the command line. Is there a way to capture the command line sent by Nautilus? 

Here is my command line:

```
sudo mount -t smbfs -o username="First Last",workgroup="WORK" "//server/users$/First Last" /media/private
```

Note the share and the username for windows have spaces (firstname<space>lastname). The error I get is something like ErrNoSuchShare (I don't have it in front of me). As I mentioned, using the same information from the menu works fine.

Any thoughts?

---

### Post by suRoot on 2005-10-31
I think you need to change your syntax.

Try:

```
sudo mount -t smbfs -o username="First Last",workgroup="WORK" "//server/users$/First\040Last"  /media/private
```

---

### Post by dbott67 on 2005-10-31
Also, if suRoot's suggestion doesn't work, try connecting just to the share (not to the user's home directory) as it seems to be where the problem lies.
```
sudo mount -t smbfs -o username="First Last",workgroup="WORK" "//server/users$"  /media/private
```
From there, you should be able to see the home directories of all users.

If it works, then you just need to get the "space" to be recognized in the user's home directory.  I'm not sure if SuRoot's example was supposed to be as it appears (i.e. **//server/users$/First\040Last**) or that the post added the **[COLOR="Red"]040[/COLOR]** (i.e. did SuRoot want the post to read **"//server/users$/First\ Last"**)

Spaces in file & directory names are always a pain! :)

-Dave

---

### Post by berbs on 2005-10-31
[QUOTE=dbott67]Also, if suRoot's suggestion doesn't work, try connecting just to the share (not to the user's home directory) as it seems to be where the problem lies.
```
sudo mount -t smbfs -o username="First Last",workgroup="WORK" "//server/users$"  /media/private
```
From there, you should be able to see the home directories of all users.

If it works, then you just need to get the "space" to be recognized in the user's home directory.  I'm not sure if SuRoot's example was supposed to be as it appears (i.e. **//server/users$/First\040Last**) or that the post added the **[COLOR="Red"]040[/COLOR]** (i.e. did SuRoot want the post to read **"//server/users$/First\ Last"**)

Spaces in file & directory names are always a pain! :)

-Dave[/QUOTE]

Your suggestion works, I can mount the user$ folder, but whenever I try to add my home folder (first last) it fails with the following error:

```
10783: tree connect failed: 
ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

I tried several options, with quotes, escaping the space or both and it does not work. I am half way there  :-)

---

### Post by suRoot on 2005-10-31
[QUOTE=dbott67]I'm not sure if SuRoot's example was supposed to be as it appears (i.e. **//server/users$/First\040Last**) or that the post added the **[COLOR="Red"]040[/COLOR]** (i.e. did SuRoot want the post to read **"//server/users$/First\ Last"**)[/QUOTE]

Sorry, I didn't even notice that.  He should only need to escape the space & **"//server/users$/First\ Last"** should do it.

---

### Post by dbott67 on 2005-10-31
Just a thought here: I'm not sure if mounting a shared directory is the equivalent of mapping a shared folder in Windows (from a technical standpoint).

In Windows, you cannot map a drive letter to a sub-folder of a share.  For example, the command:
```
net use F: \\server\users$
```
is a valid command that will map drive F: to the shared folder, however, the following command is not valid:
```
net use F: \\server\users$\subfolder
```
To test this theory, you could always create a folder in the **users$** share that does not contain spaces (or special characters; or more than 8 characters, etc.).

For example, create a folder called **test** and then use the command
```
sudo mount -t smbfs -o username="First Last",workgroup="WORK" "//server/users$/test"  /media/private
```
If it works, then we know it's the 'space' & we just need to figure out the correct syntax, if it doesn't, then we know it's because it's behaving in a similar fashion to the Windows 'map drive' command.

-Dave

---

