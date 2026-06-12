---
title: "Problem with Shell script (executing)"
date: 2008-05-25
forum: General Help
---

### Post by bobsta63 on 2008-05-25
Hi All,

Hope someone can help me out, I have written a basic shell script to automate the installation of our new set of web servers that I will be installing soon now to make my task simpler I wrote the script expecting it to execute fine however I get the following error, and yes I have chmod'd it with the correct permissions to be run as an application etc.:

> 
root@svr-mildenhall:/home/ballen/Build Scripts# ./Munin.sh [Press Return]
bash: ./Munin.sh: /bin/bash^M: bad interpreter: No such file or directory
root@svr-mildenhall:/home/ballen/Build Scripts#


The contents of my shell script is a follows:

```

#!/bin/bash

# file: Munin.sh
# location: /usr/local/bin

echo "###########################################"
echo "# Munin Quick Install                     #"
echo "###########################################"
echo ""
echo "Ready to install Web application server.."
echo ">>>>"
sleep 10;
echo ""
echo "> Enable and set ROOT password.."
sudo passwd root
echo "> Now switching into Root mode.."
su
apt-get update

sleep 5;
echo "**************************************************************************"
echo "Installing Munin for server monitoring..."
echo "**************************************************************************"
apt-get install munin munin-node

sleep 5;
echo "Installation of Munin is complete!"

```

Please can anyone give me some advise, It would appear that it can not find the interpretor but i dont know where and what line to add to the shell script to point it to the location on Ubuntu 8.04 of the interpretor...

Any help is much appreicated.

Kindest regards,
Bobby

---

### Post by cdtech on 2008-05-25
You sure you did the sudo chmod +x on the script?

---

### Post by HalPomeranz on 2008-05-25
> bash: ./Munin.sh: /bin/bash^M: bad interpreter: No such file or directory

See the "^M" in the error message above?  It looks to me like you created your shell script using a Windows text editor that introduced extra "^M" characters at the end of each line.  This extra character is being mis-interpreted as part of the path name to the shell, resulting in an invalid shell path.

Fix your script as follows:

```
perl -pe 'chomp; print "$_\n;' Munin.sh > Munin-fixed.sh
```

---

### Post by gug@fnal.gov on 2008-05-25
It sounds like it might not like the first line of the script. I wonder about the control character at the end of that line. Maybe delete the first line and retype it by hand. Where did you edit this file, I haven't seen cntl-M characters show up like that on Linux personally except when transferring files from Windows. Note it is also possible a non-printable character could be on that line too. First I would try deleting the first line and retyping by hand. If that does not work, I would try writing a new script as follows:
#!/bin/bash
echo "hi"
exit

If that doesn't work then something I don't understand is messed up. Good luck.

---

### Post by cdtech on 2008-05-25
> **HalPomeranz said:**
> See the "^M" in the error message above?  It looks to me like you created your shell script using a Windows text editor that introduced extra "^M" characters at the end of each line.  This extra character is being mis-interpreted as part of the path name to the shell, resulting in an invalid shell path.

Fix your script as follows:

```
perl -pe 'chomp; print "$_\n;' Munin.sh > Munin-fixed.sh
```

Good find Hal....

---

### Post by bobsta63 on 2008-05-25
Big thanks to you all :)

I finially figured out what it was....

It was due to the fact that I created the file in Windows as HalPomeranz said, I did try retyping the first line but it didnt work so I re-created the file on Ubuntu and now it works perfectly ... :)

Thank you all so much for you responses :D

---

### Post by koenn on 2008-05-25
besides the trailing ^M , this script probably won't work - the su will start a new (root) session, and the statements following su will not be executed in the su session. 

There's a workaround for this : replace the script with
```

#!/bin/bash
sudo apt-get update
sudo apt-get install munin munin-node

```

---

