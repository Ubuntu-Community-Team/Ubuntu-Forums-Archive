---
title: "How to start IPTABLES script automatically on boot."
date: 2008-07-03
forum: General Help
---

### Post by Avinash.Rao on 2008-07-03
Dear all,

I have configured IPTABLES on my ubuntu server and i would like run the IPTABLES script automatically when the OS boots. I am aware that i have to put this in one of the RC directories with a unique number.

1) Which RC directory should i place this script in?
2) Which startup number can i use for this script, cox this has to run after the network services start.

Thanks
Avinash

---

### Post by Gunman1982 on 2008-07-03
Directories: 3-5
startup number: you can actually configure your iptable rules before the network device is up. But I guess S24 should be fine since the dhcp client uses it too.

And you don't need to put the script into each directory, place it in in /etc/init.d/iptables and just create links with the help of 'ln'. You can see how ln works with 'man ln'

---

### Post by Avinash.Rao on 2008-07-03
Thank you for the quick reply.

Which file should i create a link to? 

or can i just for example rename the IPTABLES script file to S24iptables and put it in the rc3.d directory?

---

### Post by Gunman1982 on 2008-07-03
I would suggest doing this:
```

sudo mv iptables /etc/init.d/iptables
sudo ln -sf /etc/init.d/iptables /etc/rc3.d/S24iptables
sudo ln -sf /etc/init.d/iptables /etc/rc4.d/S24iptables
sudo ln -sf /etc/init.d/iptables /etc/rc5.d/S24iptables

```
Now if you change anything in the file /etc/init.d/iptables you don't have to think about copying it in 3 directories again.
Don't forget to make /etc/init.d/iptables executable with chmod.

---

### Post by Avinash.Rao on 2008-07-03
Thank you so much for the explanation!

Cheers,
Avinash

---

### Post by Avinash.Rao on 2008-07-05
Hi,

This didn't work. I created these link, but the output of the command iptables -L was not the same. I had to execute the script manually.

I have few questions.

1) There are startup files in the RC directory with the same S24 like S4hal. how can 2 files have the same number?

2) Do i have to create links in all the 3 RC directories? I guess just one of the RC directories should do the job.

3) The Script i am talking about is just a set of commands, most of it is iptables command to link it with the squid server.

Please help
Avinash


> **Gunman1982 said:**
> I would suggest doing this:
```

sudo mv iptables /etc/init.d/iptables
sudo ln -sf /etc/init.d/iptables /etc/rc3.d/S24iptables
sudo ln -sf /etc/init.d/iptables /etc/rc4.d/S24iptables
sudo ln -sf /etc/init.d/iptables /etc/rc5.d/S24iptables

```
Now if you change anything in the file /etc/init.d/iptables you don't have to think about copying it in 3 directories again.
Don't forget to make /etc/init.d/iptables executable with chmod.

---

### Post by cariboo on 2008-07-05
> 1) There are startup files in the RC directory with the same S24 like S4hal. how can 2 files have the same number?

As you can see by the number S4hal is not the same as S24iptables

> 2) Do i have to create links in all the 3 RC directories? I guess just one of the RC directories should do the job.


Yes it is a good idea to link it in all runlevels other that runlevel 1 and 2

> ) The Script i am talking about is just a set of commands, most of it is iptables command to link it with the squid server.

That is what most init script are, you can look at any of the files listed in /etc/init.d and view them using cat or a text editor.

Jim

---

### Post by Avinash.Rao on 2008-07-05
I am sorry, it was a typo error, i have S24HAL and S24dhcdbd? 
Yet, it didn't work, my script did execute?

> **cariboo907 said:**
> As you can see by the number S4hal is not the same as S24iptables


Jim

---

### Post by kevdog on 2008-07-05
Or you could just copy your script into the rc.local file leaving the exit at the bottom.

---

### Post by Avinash.Rao on 2008-07-05
I will try this tomorrow and let you know.

Is there anyway to run the scripts in the RC directories without rebooting. 
I know i can just execute /etc/rc3.d/S24iptables, i remember a command which runs through the RC directories.

---

### Post by Gunman1982 on 2008-07-05
> 
I am sorry, it was a typo error, i have S24HAL and S24dhcdbd?
Yet, it didn't work, my script did execute?


Yes you can have different scripts with the same number, its just an order on boot the lowest numbers are executed first and if multiple same bumbers exists I guess they execute in alphabetical order, anyway it should execute.
Make sure your script is executable  'chmod 755 /etc/init.d/iptables' and the first line in your script is '#!/bin/bash'
You can check /var/log/messages to see if there are maybe errors regarding your script.

> 
Is there anyway to run the scripts in the RC directories without rebooting. 


You can switch between runlevels with the help of the 'init' command. To make sure switch to runlevel 1 'init 1' and then back to 3-5 'init 3', 'init 4' or  'init 5'

---

### Post by Avinash.Rao on 2008-07-05
ok. I have changed the permissions of the file and created links as required. and the first line in the script is #!/bin/bash

Let me check the /var/log/messages and get back to you.



> **Gunman1982 said:**
> Yes you can have different scripts with the same number, its just an order on boot the lowest numbers are executed first and if multiple same bumbers exists I guess they execute in alphabetical order, anyway it should execute.
Make sure your script is executable  'chmod 755 /etc/init.d/iptables' and the first line in your script is '#!/bin/bash'
You can check /var/log/messages to see if there are maybe errors regarding your script.



You can switch between runlevels with the help of the 'init' command. To make sure switch to runlevel 1 'init 1' and then back to 3-5 'init 3', 'init 4' or  'init 5'

---

### Post by kevdog on 2008-07-06
If if you want to add run level scripts -- with debian the proper way to do it is with the update-rc.d executable.  I would recommend this way rather than creating a bunch of symbolic links and such.  It takes care of adding to the appropriate run levels and supplies the links.

Here are some examples:
[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by Avinash.Rao on 2008-07-06
This is good information. I will try this today and get back to you.

Thanks


> **kevdog said:**
> If if you want to add run level scripts -- with debian the proper way to do it is with the update-rc.d executable.  I would recommend this way rather than creating a bunch of symbolic links and such.  It takes care of adding to the appropriate run levels and supplies the links.

Here are some examples:
[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

### Post by sanemanmad on 2009-11-03
```
update-rc.d <name of script> defaults
```

this will make links as per below:

[HTML]root@alice:/root# update-rc.d firewall.sh defaults
update-rc.d: warning: /etc/init.d/firewall.sh missing LSB style header
 Adding system startup for /etc/init.d/firewall.sh ...
   /etc/rc0.d/K20firewall.sh -> ../init.d/firewall.sh
   /etc/rc1.d/K20firewall.sh -> ../init.d/firewall.sh
   /etc/rc6.d/K20firewall.sh -> ../init.d/firewall.sh
   /etc/rc2.d/S20firewall.sh -> ../init.d/firewall.sh
   /etc/rc3.d/S20firewall.sh -> ../init.d/firewall.sh
   /etc/rc4.d/S20firewall.sh -> ../init.d/firewall.sh
   /etc/rc5.d/S20firewall.sh -> ../init.d/firewall.sh
[/HTML]

---

