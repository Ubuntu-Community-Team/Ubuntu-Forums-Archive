---
title: "64bit Picasa?  Similar Program?"
date: 2007-08-03
forum: General Help
---

### Post by Tsu Dho Nimh on 2007-08-03
I have a large (50,000+) collection of large digital photos on multiple hard drives.  Windows Picasa has no problems with the collection.

Unfortunately I am now running 64-bit Ubuntu ... Picasa refuses to install, even though I have the 32-bit libraries.  G-thumb assumes I know where the images are ... I don't!  F-stop stops dead and closes whenever I tell it to do anything. 

How can I get Picasa working?  I'd hate to have to keep rebooting into Windows just to run it.

---

### Post by Rubadubdub on 2007-08-21
Do you still have the problem? I have 64bit Ubuntu and Picasa is running fine.

Just try to install it with "sudo dpkg -i --force-architecture picasa*.deb"

This should install Picasa just fine

If Picasa doesn't use Nautilus do the folloowing:
 Re: Anyone get Picasa to use Nautilus
This is pretty straightforward to do. First, create the hook-file.

Code:

gedit picasa-hook-filemanager.sh

In that file, paste the following in:

Code:

#!/bin/sh
nautilus "${1%%$(basename "$1")}"

Finally, copy it to a directory in the path, and make it executable:

Code:

sudo mv picasa-hook-filemanager.sh /usr/local/bin
sudo chmod +x /usr/local/bin/picasa-hook-filemanager.sh

Now, if you really don't want to do all that, and want a copy and paste to make it work, just select, copy and paste the following:

Code:

sudo echo '#!/bin/sh' > /usr/local/bin/picasa-hook-filemanager.sh
sudo echo 'nautilus "${1%%$(basename "$1")}"' >> /usr/local/bin/picasa-hook-filemanager.sh
sudo chmod +x /usr/local/bin/picasa-hook-filemanager.sh

-K
[http://ubuntuforums.org/showthread.php?t=190477](http://ubuntuforums.org/showthread.php?t=190477)

---

### Post by Tsu Dho Nimh on 2007-08-23
I'll try it and see what happens, will report back on results. 

Thanks

---

### Post by thegreenman on 2007-08-30
This worked perfectly for me. Thanks:guitar:

---

### Post by Tsu Dho Nimh on 2007-09-05
32-bit Picasa INSTALLS with this method, and even manages to show me the pictures that are on the local drives. 

Unfortunately, it can't delete pictures, move pictures, make albums or any of the other things it's supposed to do. It can't even close itself - I have to force it to quit! 

Screen redraw is extremely slow - it takes several minutes to close or change the image, or it freezes.  I do not get any error messages, it just doesn't work!

HARDWARE:
64-bit Ubuntu 7.04
AMD Athlon, 2GB RAM
NVidia GeForce7600

And for reasons known only to Ubuntu ... it did not install in usr/local/bin  ... it's in /opt/picasa  

Maybe if I move it things will work?

---

