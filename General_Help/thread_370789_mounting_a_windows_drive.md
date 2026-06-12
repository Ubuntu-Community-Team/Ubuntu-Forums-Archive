---
title: "mounting a windows drive"
date: 2007-02-26
forum: General Help
---

### Post by g0l3m on 2007-02-26
Hello all,

I've recently switched to Ubuntu from Fedora and I have to say, I'm quite impressed so far.
However, I'm having some teething problems.
To mount a win drive under FC6 I used to do:

mount //172.16.3.145/C$ /home/blah/winC/ -t cifs -o user=foo,domain=bar

This would ask for my "bar" domain pass for user "foo" and then mount the drive.
Unfortunately, under Ubuntu (6.10), I'm getting this instead:

mount: block device //172.16.3.145/C$ is write-protected, mounting read-only
mount: cannot mount block device //172.16.3.145/C$ read-only

It doesn't ask for a pass or anything...it just fails.
Any ideas?

Thx in advance,
g.

---

### Post by PgR on 2007-02-26
I've noticed the same thing.

Don't know if it helps, but in my case... 
It's failing 'cos it's getting a logon failure from the windows box.
It seems it isn't prompting for a password.
if I add ,password=<windows_password_here> then it'll work; assuming that the windows user has a password, of course.

But the real question is "why doesn't it prompt"

---

### Post by dmizer on 2007-02-26
have you installed smbfs?
```
sudo aptitude install smbfs
```

---

### Post by kpkeerthi on 2007-02-26
Yeah... install smbfs and then... ```
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```

---

### Post by g0l3m on 2007-02-27
Aha!!! Success!!!
smbfs was not installed...
Now everything works the way it used to...i.e. I type:

mount //172.16.3.145/C$ /home/blah/winC/ -t cifs -o user=foo,domain=bar

it then asks for a pass, and mounts the drive properly.

Thx for the tip guys,
g.

---

### Post by PgR on 2007-02-27
Excellent!

How odd, though. Install smbfs and it still errors on -t smbfs but works with -t cifs.

Not sure I understand that, but it works - so thanks chaps.

---

### Post by dmizer on 2007-02-27
g0l3m,

if you would ... please edit your first post, and mark the situation as resolved so people know that they can find an answer here.

thanks,
enjoy.

---

### Post by g0l3m on 2007-02-28
done!

---

