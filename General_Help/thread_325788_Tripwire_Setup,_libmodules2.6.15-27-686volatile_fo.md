---
title: "Tripwire Setup, /lib/modules/2.6.15-27-686/volatile/ folder looks out of place???"
date: 2006-12-26
forum: General Help
---

### Post by dannyboy79 on 2006-12-26
I am trying to setup Tripwire, just using the default policy config file I get errors about 4 different objects being on different file systems? This is what it states:
The object: "/lib/modules/2.6.15-27-686/volatile" is on a different file system...ignoring.
The object: "/dev/.static/dev" is on a different file system...ignoring.
The object: "/dev/pts" is on a different file system...ignoring.
The object: "/dev/shm" is on a different file system...ignoring.	

Also, I get about 30-40 errors about files and or directories that don't exist. Some of them include:
### Warning: File system error.
### Filename: /root/.bash_profile
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.bash_logout
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.amandahosts
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.addressbook.lu
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.addressbook
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.Xresources
### No such file or directory
### Continuing...
### Warning: File system error.
### Filename: /root/.Xauthority
### No such file or directory
### Continuing...

I read online that the reason I am getting the errors about the different file ssytem thingy is because Tripwire currently can't follow symlinks. I am very new to linux and I thought I knew what  symlink was but if tripwire has read thru my whole system and is telling me that I only have 4 symlinks, that doesn't sound correct, does it?? I mean, I can say for sure I never added any intentionally but it's just when I am browsing around within a terminal and doing ls -la I'll see this once in awhile,  build -> /usr/src/linux-headers-2.6.15-27-686isn't this a symlink? If this is true, than why didn't this come up as an error? 

Then the other errors are because I simply don't have that file or dir on my computer. Which isn't a bad thing I just have to comment those checks out b4 I create the database file. But shouldn't I have a /root/.bash_profile file? I haven't enabled the ability to log in as root so I thiunk that's why I don't have a /root/.Xauthority file or like the /root/xsession-errors file. Am I correct in what I am saying?

Then I jujst wanted to ask what's up with that volatile folder? What is it there for, there is a weird empty file in there called .mounted and chkrootkit always states that this is a suspicious files and dirs along with all these others.
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/lib/modules/2.6.15-27-686/volatile/.mounted

I have read that the /usr/lib/jvm/ is usually a false-positive but what about this .mounted file that's empty? I know it's empty because I used the command "file" on it. that should tell me what 'type'  of file it is, correct? Anyway, any help would be much appreciated. Thanks

---

### Post by dannyboy79 on 2006-12-29
can't believe not one person uses tripwire? anyone help me?

---

### Post by dannyboy79 on 2007-01-05
waited 6 days this time, please?

---

### Post by dannyboy79 on 2007-01-16
bump again. Can someone at least tell me if they have a folder named volatile on their system anywhere?

---

### Post by robbie75 on 2007-07-04
Hi,
I've got the "volatile" directory on a fresh installed feisty server...
Moreover, I have a file named .mounted under that directory
and chkrootkit is complaining about that; the file is empty...
BTW seems that the chkrootkit warning in this case is a false positive.


Regards
Robbie

---

### Post by dannyboy79 on 2007-07-05
well thank you for responding so I know that I am not the only person getting this. I chalked it up to false positive as well. thanks again for the info despite it being 6 months later.

---

