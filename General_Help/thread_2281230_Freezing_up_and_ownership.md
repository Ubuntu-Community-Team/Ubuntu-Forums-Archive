---
title: "Freezing up and ownership"
date: 2015-06-05
forum: General Help
---

### Post by HEARD on 2015-06-05
So I downloaded and installed the latest stable build for Ubuntu Desktop.

I got it running no problem.
Now I am having ownership problems that is forcing me into nautilus and altering each file individually which is a real pain.

Is there any way to set the default owner of each file to myself and give myself ownership rather than just administrator?



Also as per my other issue: I may have solved it but I'll still throw it out there I haven't been home to find out.
After about 3-5 minutes of Ubuntu running it will freeze up. I can move my mouse for the first minute but that is literally it. After that the mouse will disappear and it's completely frozen.

Thoughts?

---

### Post by The Cog on 2015-06-05
> **HEARD said:**
> Is there any way to set the default owner of each file to myself and give myself ownership rather than just administrator?
Yes, but it will never boot again until you reinstall.

You should have ownership of all the files inside your home folder (/home/your-name). If you don't, we can help you there.

For files outside your home folder, they are all system files, not user files. You need to be able to mentally separate working as yourself (as a user) and working as the system administrator (root). Read this for how to gaind the priviledges when you need to do sysadmin work: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


> 
Also as per my other issue: I may have solved it but I'll still throw it out there I haven't been home to find out.
After about 3-5 minutes of Ubuntu running it will freeze up. I can move my mouse for the first minute but that is literally it. After that the mouse will disappear and it's completely frozen.
Sorry, but I can't help you with that one.

---

### Post by pfeiffep on 2015-06-05
I suggest reading [this]("http://unix.stackexchange.com/questions/1314/how-to-set-default-file-permissions-for-all-folders-files-in-a-directory") concerning file permissions

---

### Post by HEARD on 2015-06-05
> **The Cog said:**
> 
You should have ownership of all the files inside your home folder (/home/your-name). If you don't, we can help you there.


Which should include my desktop and anything on it right? Because even those files I don't have ownership of.

I'm not concerned as much with system files as I don't have a need to be messing with those at the given moment.
It is a fresh install so I wouldn't be upset if I had to reinstall ubuntu.

---

### Post by HEARD on 2015-06-05
> **pfeiffep said:**
> I suggest reading [this]("http://unix.stackexchange.com/questions/1314/how-to-set-default-file-permissions-for-all-folders-files-in-a-directory") concerning file permissions

Thank you :]

---

### Post by QIII on 2015-06-05
Hello!

If you have been randomly changing permissions on files you don't own, your goose may already be cooked.

To tag on to The Cog --

Even though you may have set yourself up as the Administrator account when you installed, you still aren't the owner of the some files.  Root is.  If you want to modify system files (be very careful!), you still have to elevate your privileges.

Don't start just changing ownership of things outside your /home.

What on your "desktop" are you finding you don't own?

---

### Post by HEARD on 2015-06-05
I haven't altered any system files or anything of the sort; but I don't have the ability to even delete folders/files from my desktop.

---

### Post by QIII on 2015-06-05
Do you have an example?

---

### Post by HEARD on 2015-06-05
I'm at work right now, when I get home I'll attempt to provide an example.

---

### Post by The Cog on 2015-06-05
> **HEARD said:**
> Which should include my desktop and anything on it right? Because even those files I don't have ownership of.
Yes it should. There is somethign amiss if you don't own those. In fact, it should not be possible to create files that you don't own.

It might help if we can see a listing of the contents of your home directory - particularly the files that are causing trouble. And it would help to know your username too. Can you post the output of the command ```
ls -l
``` so we can see some of the troublesome files? Knowing how they get there might help too, if you know.

---

### Post by Guy_Wood on 2015-06-05
I experieced the 'freezing up within a couple of minutes of startup' issue. Turns out it was the graphics driver, I installed the nvidia drivers from the Xorg ppa and it's fine now.

---

### Post by pfeiffep on 2015-06-05
The advice given thus far is spot on, but I have questions...

"How many userids did you create when installing or subsequent? and are you possibly confusing  Linux administrator with Windows administrator? 

Your default userid in Ubuntu can assume administrator privilege with the use of sudo.

---

