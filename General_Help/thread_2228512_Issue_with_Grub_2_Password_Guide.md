---
title: "Issue with Grub 2 Password Guide"
date: 2014-06-07
forum: General Help
---

### Post by dolomite7922 on 2014-06-07
Ok I followed this guide:

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

and all I did was add this line:

cat << EOF
set superusers="user1"
password user1 password1
EOF

to file:

[I]/etc/grub.d/00_header

So now everytime that the computer boots it asks for a username and password.  I changed my mind and do not wish to have this feature so I loaded the file again and deleted that command entry.  I thought everything would go back to normal, I was wrong!  It didn't change anything so I am stuck and I am looking for assistance as to how to remove this username and password nagging me everytime it boots even though I have deleted the command out of the file.


Any assistance would be greatly appreciated.

Thank you

Gordon
[/I]

---

### Post by SantaFe on 2014-06-07
After editing the file, did you open a terminal & run *sudo update-grub?*

I know anytime I make any changes to GRUB2, I always have to do that so grub will see the changes. ;)

---

### Post by dolomite7922 on 2014-06-07
That worked thank you!

---

### Post by SantaFe on 2014-06-08
Glad it worked. ;)

---

