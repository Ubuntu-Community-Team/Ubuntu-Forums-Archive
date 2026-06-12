---
title: "Permission denied with root"
date: 2014-05-08
forum: General Help
---

### Post by darko4 on 2014-05-08
Hi all,

I'm having problem with -bash [COLOR=#ff0000]./some_app.run: Permission denied[/COLOR] ...

I've downloaded some_app from the internet and saved it to external USB disk, done ```
chmod +x some_app
``` also with root account, but when i try to execute it i get 'permission denied...

Any help?

Thank you,
Darko

---

### Post by jdeca57 on 2014-05-08
I often wonder what people mean when they say they use the root account in Ubuntu. I mean, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) tells how to do that but using root isn't exactly standard. A first thing would be to put some_app in the home directory and use commands like chown or chmod and run it. And then, if that works, try it on an external drive.

---

### Post by papibe on 2014-05-08
Hi darko4.

If the USB disk is formated with NTFS, chmod won't do anything as NTFS does not support Linux permissions.

There are 2 solution I can think of:
[LIST]
[*]Remount the drive so that it include the execution permission in all files, or
[*]Load manually the executable using the dynamic loader:
[LIST]
[*][*]In a 64 bit system:
```
/lib64/ld-linux-x86-64.so.2 /path/to/some_app
```


[*][*]In a 32 bit system:
```
/lib/ld-linux.so.2 /path/to/some_app
```
[/LIST]
[/LIST]
Hope it helps. Let us know if you how it goes and if you want some help remouting the USB disk.
Regards.

P.S.: do not use sudo to load 'some_app'. Try it running it as the regular user.

---

### Post by darko4 on 2014-05-08
> **jdeca57 said:**
> I often wonder what people mean when they say they use the root account in Ubuntu. I mean, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) tells how to do that but using root isn't exactly standard. A first thing would be to put some_app in the home directory and use commands like chown or chmod and run it. And then, if that works, try it on an external drive.

Yes, when 'I' say i'm running it as root that means i'm running it by prefixing the command with 'sudo'.

Putting it to home directory and chmod +x worked here, and thank you for that.

Regards, 
Darko

---

### Post by darko4 on 2014-05-08
> **papibe said:**
> Hi darko4.

If the USB disk is formated with NTFS, chmod won't do anything as NTFS does not support Linux permissions.

There are 2 solution I can think of:
[LIST]
[*]Remount the drive so that it include the execution permission in all files, or 
[*]Load manually the executable using the dynamic loader:
[LIST]
[*]In a 64 bit system:
```
/lib64/ld-linux-x86-64.so.2 /path/to/some_app
``` 
[*]In a 32 bit system:
```
/lib/ld-linux.so.2 /path/to/some_app
``` 
[/LIST]
  
[/LIST]
Hope it helps. Let us know if you how it goes and if you want some help remouting the USB disk.
Regards.

P.S.: do not use sudo to load 'some_app'. Try it running it as the regular user.


Yes, it's formatted as NTFS, so...
The 'trick' from the previous post by jdeca57 helped, and I'm satisfied with that, so I won't be using your code, which is kinda to much right now. Newbie, what can I say :)...

Thanks,
Darko

---

