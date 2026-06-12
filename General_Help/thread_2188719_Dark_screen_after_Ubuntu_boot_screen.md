---
title: "Dark screen after Ubuntu boot screen"
date: 2013-11-18
forum: General Help
---

### Post by aleksandar.rachkov on 2013-11-18
Hi,

This question may have been answered previously, but given that I don't know what is wrong with it, I am posting in this thread.

My idiot friend decided to mess with my laptop and did something he does not know exactly what. He says he was trying to change my password. He was following the instructions on the following link:
[https://ifconfig.dk/ubuntu/](https://ifconfig.dk/ubuntu/)

So, I caught him in action and we manually rebooted the laptop (step 14 of the guide).
After the reboot and the UBUNTU boot screen, it went to command prompt asking my login and password. When I entered my usual ones, nothing happened. So I rebooted again.

Now, after the boot screen, there is only a black screen.

Does anyone have any idea how to fix this? Ultimately, I can reformat and re-install UBUNTU, but I'd like to keep that as my last solution.

Thank you in advance.

---

### Post by Bashing-om on 2013-11-18
aleksandar.rachkov; Well, these things happen,
Let it be a lesson in the learning curve.
With no telling what may have been done to the system while messing about with the "root" access, the end is uncertain.

For starters, I suggest that you see about changing your password and see if you can access your system:
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Then, get a very rough idea of the system stability by seeing what the package manager sees:
Terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
If that runs clean, then resume using the system normally and see what results .. keeping backups of all data is always a good practice, now is a great time to implement that practice !

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by aleksandar.rachkov on 2013-11-18
Alright, so I was able to boot into terminal and then reinstall the video drives. Somehow they have messed up throughout that procedure.

Thanks for the help, Bashing-om!

---

### Post by Bashing-om on 2013-11-18
aleksandar.rachkov; Hey, You do the good work !

I had not even got to the point of looking at the graphics drivers !
If you are confident that your system is now stable, please mark this thread as solved. That aids others seeking a similar solution, and helps keep the forum tidy.

And, we will have another adventure another day.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

