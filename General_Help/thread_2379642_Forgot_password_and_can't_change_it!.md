---
title: "Forgot password and can't change it!"
date: 2017-12-07
forum: General Help
---

### Post by laserine on 2017-12-07
Hello!

I forgot my password and can' get into my laptop.
I already tried going into recovery mode and all that but it does not work.
it just says:
Authentication token manipulation error
password unchanged
I think it has something to do with the fact that it is a Windows machine but Win. broke and it got Ubuntu but I downloaded kubuntu and couldn' figure out how to delete Ubuntu. But not sure.

If someone could help, that would be great!

---

### Post by VMC on 2017-12-07
I'm guessing its not your laptop password, but ubuntu. Have you seen this: "[COLOR=#000000][Authentication token manipulation error]("https://askubuntu.com/questions/91188/authentication-token-manipulation-error")"[/COLOR]

---

### Post by laserine on 2017-12-08
Well took a look and what a surprise, I can' understand it.
also the mounting command doesn't work. At least that's what I think.

---

### Post by leunam12 on 2017-12-08
When you boot to recovery your filesystem is mounted read-only, it has to be mounted read and write for you to be able to make changes ```
mount -rw -o remount / 
```

---

### Post by laserine on 2017-12-08
Hello!
I am quite aware of this.
The problem is it doesn't work.

---

### Post by QIII on 2017-12-08
Hello!

What do you mean by "it doesn't work"?  Do you get a message?  Does nothing appear in the terminal?

Try

```
mount -o remount,rw /
```

Note that there are no spaces before or after the comma.

---

### Post by laserine on 2017-12-09
Well I don't think it works either.
If I understand correctly, I don't want a # because that means read-only but a $ means read-write. 
Not sure though.
And to answer your question, no. Nothing appears or changes.

---

### Post by deadflowr on 2017-12-09
> If I understand correctly, I don't want a # because that means read-only but a $ means read-write. 
No
# means that the current user is root.
$ means the current user is a non-root user.
> I think it has something to do with the fact that it is a Windows machine but Win. broke and it got Ubuntu but I downloaded kubuntu and couldn' figure out how to delete Ubuntu. But not sure.

What's what?
From a rather armchair read of this it might be the hard drive or file system is corrupt.
See if running the fsck option in recovery mode helps.
If not, since Windows fell apart it could be a bad disk.
But that's pure speculation on my part.

---

### Post by laserine on 2017-12-10
Thank you, that worked!

---

### Post by davehk on 2017-12-10
> **laserine said:**
> 

And if #/$ don' mean that, then how do I know it' in read-write mode?

```

dave@namrok3:~$ mount  | grep '/ '
/dev/mapper/ubuntu--vg-root on / type ext4 ([COLOR="#FF0000"]rw[/COLOR],relatime,errors=remount-ro,data=ordered)


```

note the "rw"
the "/dev/mapper.,..." will be replaced by the ID of your disk.

---

### Post by deadflowr on 2017-12-10
What worked?

---

