---
title: "Samba with XBox Media Center from EXT3"
date: 2008-03-10
forum: General Help
---

### Post by rugbert on 2008-03-10
So I've gone and mostly successfully set up Samba on my PC to share movies and music to my Xbox running XMBC.

But I can only share files off a NTFS drive. Not my ext3 file system.

See, I have an external with some media on it and I set the public path to that of the external with NTFS, however when trying to access anything in my home directory (and yes, I changed browseable to yes in the [homes] section) I get this error:

error: 1073741772
Share Not Available.

even if its something not in my home directory I get the error. Ive already tried putting the user name and password in the xml file and that doesnt work. I just CANT share files from ext3. I guess I could try to use another file system tho.

---

