---
title: "Ubuntu start up error"
date: 2016-06-24
forum: General Help
---

### Post by Ben_E on 2016-06-24
Hello this started Saturday and still keeps happening every time i start the PC. Can someone give a fix . Thank you
 
here is the photo of the error code.

[https://drive.google.com/open?id=0B2vUtuyhh2HlTUQyQ1FMTWtUc28](https://drive.google.com/open?id=0B2vUtuyhh2HlTUQyQ1FMTWtUc28)

Sorry about the photoquality

---

### Post by westie457 on 2016-06-24
Hi,
Do you get a Grub menu at boot time or does your machine go straight to the error?

This is one way to fix it, there probably are others.

Boot your machine and immediately start tapping the Esc key or the left Shift key to force the Grub menu to show.
In the Grub menu choose the second line (advanced options) hit Enter, then in the new screen pick the first line that has recovery in it.

After a few moments a Window pops up, here choose FSCK hit enter.
Let this finish, at the bottom of the window will be a prompt, follow those directions.

When all is done and you are back to the main window select Drop to Root Prompt, type in reboot and then hit Enter.


Now you should be back to your normal system.

---

### Post by Ben_E on 2016-06-24
ok i did the steps here is the new error

[https://drive.google.com/file/d/0B2vUtuyhh2HlQXpZMnFpeWk2bTQ/view?usp=sharing](https://drive.google.com/file/d/0B2vUtuyhh2HlQXpZMnFpeWk2bTQ/view?usp=sharing)

---

### Post by Ben_E on 2016-06-24
i forgot to reply

---

### Post by westie457 on 2016-06-27
Have been afk for the weekend.
Attempt number 2.

In the Root command line of Recovery mode ```
fsck -fay
```
The 'f' forces a check even if the system is clean. The 'a' is automatic for repairs that need no user input. The 'y' assumes yes for everything else.

when 'fsck' has finished with no errors reboot the system to normal.

---

### Post by Ben_E on 2016-06-27
When i type that it says fsck from until-linux 2.27.1

---

### Post by westie457 on 2016-06-27
Sorry that was my bad, tried the command now and got a message similar to yours and with 'e2fsck : Only one of the options -p/-a, -n or -y may be specified.'

Suggest you run the command without the -y first and without the -a options.

Running either by itself may be enough.

Let us know how it goes.

---

### Post by Ben_E on 2016-06-27
what do i do from here?

[https://drive.google.com/file/d/0B2vUtuyhh2HlS3hOVU96TThQYUU/view?usp=sharing](https://drive.google.com/file/d/0B2vUtuyhh2HlS3hOVU96TThQYUU/view?usp=sharing)

---

### Post by X-RED_Tech on 2016-06-27
```
e2fsck -p /dev/sda1
```

You always need to specify the path to the partition you want checked and repaired.
Be prepared for a failing drive scenario. There's no software/commands to fix a physically broken drive.

---

### Post by Ben_E on 2016-06-27
does this means its broken ? 

[https://drive.google.com/file/d/0B2vUtuyhh2HlbkZnZ1FrcjhEMVE/view?usp=sharing](https://drive.google.com/file/d/0B2vUtuyhh2HlbkZnZ1FrcjhEMVE/view?usp=sharing)

---

### Post by X-RED_Tech on 2016-06-27
Try again without the -p argument as the message says.
It'll ask a lot of questions. Answer yes to all.

---

### Post by Ben_E on 2016-06-27
I was able to log on to the laptop . And was able to retrieve the files it no longer wants to start up . looking into it there was a ant infestation next to the hard drive.

---

### Post by DuckHook on 2016-06-27
I don't want to flood you with suggestions here, but in cases like these, it is critical that you backup your data *right now*. If you are lucky, it will just be a few corrupted files from, say, an incomplete shutdown or previous power drop, but if you are unlucky, as per X-RED, you are facing a potentially wonky HDD on its last legs. For any problem that concerns a HDD/SSD, the first step is to backup your data.

*EDIT*

Post rendered moot by OP's discovery and actions.

---

