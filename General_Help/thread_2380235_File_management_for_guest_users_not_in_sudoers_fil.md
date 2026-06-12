---
title: "File management for guest users not in sudoers file"
date: 2017-12-14
forum: General Help
---

### Post by kolinab on 2017-12-14
I've built an ubuntu based machine in a public computer/lab setting. I will configure restricted user accounts and enable a logout timer,  (timeoutd) which automatically logs users out after their time has elapsed. I will use a script to restore the user's /home to its original state. I want those files to be wiped on each logout for privacy reasons. I would enable and use the guest session, except I need to enforce a 30 minute time limit for some users, and a 60 minute time limit for other users.

**Occasionally before a user's session timer is up, I would like to be able to intervene in the user session and save their files to a folder that will not be wipe**d. I am fine with using sudo on the command line to copy any files to another user's home or to a location on "/". But my user is not in the sudoers file. I don't especially want to add my 'guest' users to the sudo group, even though those users won't be supplied with the password.

I'd also like to occasionally bypass the logout timer for similar reasons - I had thought of just killing the timeout daemon process, but I need sudo to start and stop processes, don't I?

Is there a smarter way to do this?

---

### Post by yancek on 2017-12-14
> But my user is not in the sudoers file. 

Why not?  If you are creating this setup on your machine for your business or employer, why would you not have sudo right?

>  I am fine with using sudo on the command line to copy any files to another user's home or to a location on "/". 

You would not need sudo right to copy data FROM another location, you would need to be the owner of the directory you are copying TO,  another user /home directory.

>  don't especially want to add my 'guest' users to the sudo group, even though those users won't be supplied with the password.


I'm not understanding why you think the guests who are using your machine for a fee (?) would need any sudo right.  You or the admin would have all the rights to access and copy from the guest directories to save whatever files you want.

---

### Post by kolinab on 2017-12-14
> **yancek said:**
> Why not?  If you are creating this setup on your machine for your business or employer, why would you not have sudo right?



You would not need sudo right to copy data FROM another location, you would need to be the owner of the directory you are copying TO,  another user /home directory.



I'm not understanding why you think the guests who are using your machine for a fee (?) would need any sudo right.  You or the admin would have all the rights to access and copy from the guest directories to save whatever files you want.

Thank you for the reply and considering my situation. I didn't do a very thorough job of explaining my situation. 

The computer will be a station in a public library. I am the Administrator. If someone wants to use the computer, they ask me and I physically log them in to the 'adult' or 'kids' account using the password for those accounts. I have four accounts on the system:

administrator
adult
kids
testing

The adult and kids accounts will both be logged off after a specified time limit using timeoutd. I'll figure out a script to wipe /home/adult and /home/kids on each logout. I haven't solved that issue yet.

What often happens is that someone will come to me in a panic when their time is nearly up, having not saved or sent their work before the system logs them out. /home/adult will be wiped when they are logged out but I just want to save their 'resume.doc.' So I walk up to the machine and 'adult' is logged in. I want to ```
sudo cp /home/adult/resume.doc /home/special/resume.doc
```

But the user is not in the sudoers file. I guess I should just add the user to the sudoers file but I wasn't sure if there was a good reason not to. I'm happy to consider any solution to make this work nicely - once I get it right on this system I'm going to replicate it on 4 more just like it. 

Please let me know if I'm not explaining myself well. I had considered a kiosk specific distribution, but I am familiar with ubuntu (I'm actually using lubuntu) and I think it will allow me more flexibility.

---

### Post by kolinab on 2017-12-20
Found my answer. Add the users to sudoers. Marking as solved.

---

