---
title: "Symbolic Link - How secure is it"
date: 2007-10-08
forum: General Help
---

### Post by Scorpuk on 2007-10-08
I have created a symbolic link in my var/www folder to a file in my home folder /home/john.

ie:

sudo ln -s /home/john/file.txt /var/www/.file.txt


I have also made the file hidden by adding a period infront of it so Apache doesnt display it within a browser.


Is my system still as secure as it was before I made this link or has this potential to open up my computer?

---

### Post by kidders on 2007-10-09
Hi there,

Occasionally, bugs involving symlinks do crop up, and they invariably have security implications. So, I suppose it's theoretically possible that a symlink might allow an unintended degree of access to your system, but only within the bounds of your file access permissions ... so it's important to check that they're sane.

That aside, for Apache to access a file in your home directory, you would normally have to "chmod o+x" it, which essentially grants the whole world access to it. Under those circumstances, it would be important to check that none of the file access permissions within your home directory are inappropriately loose.

Prefixing a filename with a dot has no impact on anything. Again, I suppose, the important thing is to check that access to your files is properly controlled by the permissions you set.

I hope that helps. As you probably know, most Apache users like to configure it not to dereference symlinks. This isn't because they are somehow inherently "insecure" ... but they are designed to create file access scenarios that aren't always immediately obvious, and most server admins just prefer not to have to think about them.

---

### Post by Scorpuk on 2007-10-09
tnx for the response.



The file I have created the symlink to is a plain text file. I have not chmod'd it with anything and can access it. It is my Folding @ home status file. :-)

I have changed no access rights to anything within my home folder so I presume everything else should be secure, not that there is much in it anywho.

---

### Post by kidders on 2007-10-09
> **Scorpuk said:**
> I have changed no access rights to anything within my home folder so I presume everything else should be secureThat's not a safe assumption. Since your home is presumably "chmod o+x" at the very least (to make your symlink work), you might as well give it the once over.

---

