---
title: "How to use LIbreofficeCalc with firejail ?"
date: 2018-09-17
forum: General Help
---

### Post by linuxyogi on 2018-09-17
Hi,

I already use firejail to sandbox FF, Thunderbird, Hexchat, etc. I have added firejail to the .desktop files.

I want to use it with LibreofficeCalc too.

In short what I want to do is when I click on a .ods file I want LibreofficeCalc to launch 

within the firejail sandbox.

How can I do this ?

---

### Post by Claus7 on 2018-09-20
Hello,

have you right clicked an .ods file and then go to properties and from the selected applications choose a custom command?

From there write the command:
firejail libreoffice --calc

Is it working that way?

Regards!

---

### Post by linuxyogi on 2018-09-20
> **Claus7 said:**
> Hello,

have you right clicked an .ods file and then go to properties and from the selected applications choose a custom command?

From there write the command:
firejail libreoffice --calc

Is it working that way?

Regards!
[ATTACH=CONFIG]281133[/ATTACH]


(Click to enlarge)

As you can see there is no "choose a custom command".

---

### Post by Claus7 on 2018-09-20
Hello,

in lubuntu 18.04 there is no such problem. 

If scrolling down, can you see any additional option? Maybe that way the add button will be enabled so as for you to add the custom command.

At least you could try it first from the command line to see if it is working:
firejail libreoffice --calc name_of_ods_file

Regards!

---

### Post by linuxyogi on 2018-09-20
> **Claus7 said:**
>  At least you could try it first from the command line to see if it is working:
firejail libreoffice --calc name_of_ods_file 

Yes that's working.

---

### Post by Claus7 on 2018-09-21
Hello,

> **linuxyogi said:**
> Yes that's working.

good! Now, can you follow this link:
[https://askubuntu.com/questions/789476/how-to-create-my-own-terminal-commands](https://askubuntu.com/questions/789476/how-to-create-my-own-terminal-commands)

and check again if you can see the script's name under the available commands (as in your screenshot)?
By selecting it this way it should work.

EDIT:
In case it does not and you are using nautilus, then you could follow this link instead:
[https://askubuntu.com/questions/431703/how-to-add-open-with-custom-command-option-in-right-click-menu-of-nautilus](https://askubuntu.com/questions/431703/how-to-add-open-with-custom-command-option-in-right-click-menu-of-nautilus)

Regards!

---

