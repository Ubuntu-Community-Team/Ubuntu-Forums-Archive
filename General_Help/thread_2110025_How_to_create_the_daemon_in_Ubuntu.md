---
title: "How to create the daemon in Ubuntu?"
date: 2013-01-29
forum: General Help
---

### Post by James127 on 2013-01-29
Hi all,

I'm trying to create the daemon in Ubuntu and it still doesn't work. :(

I created the java file (it will create the new .txt file and auto increase the number in this .txt file) then I conversed to "myJava.jar" file.

After that I created the abc.sh file to active above "myJava.jar" file. Then I put .sh file into /etc/init.d/abc dictionary by the script below: 

[COLOR=Red]sudo[/COLOR] mv abc.sh /etc/init.d/abc
[COLOR=Red]sudo[/COLOR] chmod +x /etc/init.d/abc
[COLOR=Red]sudo[/COLOR] update-rc.d abc defaults


In the current, I only start my daemon by terminal by script: [COLOR=Red]

sudo[/COLOR] /etc/init.d/abc start[COLOR=Black]

So, how can I do it will be activated automatically when my PC start up instead I start it by terminal in current? :(

I found the many info on the internet but I can't figure out. Everybody can help me!!!

Thanks alot, 
James.
[/COLOR]

---

### Post by rnerwein on 2013-01-29
> **James127 said:**
> Hi all,

I'm trying to create the daemon in Ubuntu and it still doesn't work. :(

I created the java file (it will create the new .txt file and auto increase the number in this .txt file) then I conversed to "myJava.jar" file.

After that I created the abc.sh file to active above "myJava.jar" file. Then I put .sh file into /etc/init.d/abc dictionary by the script below: 

[COLOR=Red]sudo[/COLOR] mv abc.sh /etc/init.d/abc
[COLOR=Red]sudo[/COLOR] chmod +x /etc/init.d/abc
[COLOR=Red]sudo[/COLOR] update-rc.d abc defaults


In the current, I only start my daemon by terminal by script: [COLOR=Red]

sudo[/COLOR] /etc/init.d/abc start[COLOR=Black]

So, how can I do it will be activated automatically when my PC start up instead I start it by terminal in current? :(

I found the many info on the internet but I can't figure out. Everybody can help me!!!

Thanks alot, 
James.
[/COLOR]
hi
i guess when you will start your script from a terminal you will be asked for a password ?
did you have an entryp in your /etc/sudoers like: 
 your_usr_account ALL=NOPASSWD: abc_start

and the dependencies to start your script.
let's see the ouput of your file in /etc/init.d for further information
cheers

---

### Post by James127 on 2013-01-29
Thanks for your help, rnerwein.

I found the other way that I will append the script (the script calls my java file) into the [COLOR=Blue].profile[/COLOR] file in the Home folder. Then I restarted my Ubuntu and it auto worked.

James.

---

