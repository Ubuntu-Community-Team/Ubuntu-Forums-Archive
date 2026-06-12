---
title: "Admin user cant see DVD Rom but standar users can"
date: 2012-10-19
forum: General Help
---

### Post by panafff on 2012-10-19
Hello community, I am openning a new post since I am not be able to resolve my problem with a DVD rom. I am able to see the DVD rom device on any standar user session of my Ubuntu 12 system but I dont see it while I am logged in to the administrator account. I dont see it in Home folder and when I go to my media folder I can but the folder has an x at the right bottom and if I click on it I got this message: "You do not have the permissions necessary to view the contents of DVD CONTENTE HERE".

What can I do to recover the access to my DVD rom since I was able to access it without problems before? Thank you in advanced for any help you can provide me!

---

### Post by dniMretsaM on 2012-10-19
I think you have to be [FONT=Courier New]cdrom[/FONT] group. Run the command [FONT=Courier New]groups[/FONT] to find out if you're in said group (if you are, it's obviously a different issue).

If you are not in the [FONT=Courier New]cdrom[/FONT] group, you can add yourself with this command:
```
sudo usermod -a -G cdrom [username here]
```Be sure to use the [FONT=Courier New]-a[/FONT] option or you will remove yourself from all other groups.

---

### Post by panafff on 2012-10-19
Hey dniMretsaM thank you for replying, I did what you suggested and I received this ouput "user Euclides (admin) does not exist" what it does not make sense, I then discovered in the user accounts settings that my user had a "locked" status in the upper right corner so I clicked there and then I was able to see the content of the DVD rom. I am not really sure what happended but its good to know that my issue has been resolved.

Thank you again, cheers!

---

