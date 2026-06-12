---
title: "Setuid. Sudo errors because of chmod?"
date: 2006-12-19
forum: General Help
---

### Post by boogiepop88 on 2006-12-19
So earlier today i was trying to take ownership of the /usr folder using chmod now anytime i try to sudo it returns this: 

sudo: must be setuid root

Can anyone explain why this changed and how to fix it?  :confused: 

I couldn't find a good thread in search.

---

### Post by jrib on 2006-12-19
did you recursively change the permissions in /usr?
What command did you issue exactly?
What does ```
ls -l $(which sudo)
``` return?

Permissions outside of HOME shouldn't really be touched, especially not recursively.

---

### Post by boogiepop88 on 2006-12-20
indeed i did. recursively with a 755? which i thought wouldnt mess anything up, just give me the ability to write to it. reason being the pixmap folder, so i could write to it and keep all my icons in one place.  I'm an intermediate linux user i would say, but a lot of things involving folder permissions are still a bit fuzzy. is there a way i can reverse this due to my lack of being able to sudo? or just change it back normal and ill just make a folder to hold icon sets?  ](*,)

---

### Post by jrib on 2006-12-20
You're looking at a reinstall.  I can tell you what the permissions are on /usr/bin/sudo, but I would reinstall if I were you.  It's impossible to reverse that command since the previous permissions aren't remembered anywhere.  The problem is that other files in /usr may need certain permissions for your programs to operate correctly.

Here are the permissions on /usr/bin/sudo anyway:
```

-rwsr-xr-x 2 root root 91508 2006-10-09 07:37 /usr/bin/sudo

```

If you need root access, select "recovery mode" from the grub menu when you boot up.

If I were in your position, I would backup anything I needed to and reinstall.  Once you reinstall to take care of this issue, you should use sudo to get access to things not in /home that you need access to.  I think you should just hold your icons somewhere in your $HOME in this case.

On a side note, here is a good introduction to permissions on linux: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by boogiepop88 on 2007-01-01
/sigh i was afraid that was the answer i was going to get.


thanks so much for the help!  it seems i need to read that permissions intro  :-k

---

