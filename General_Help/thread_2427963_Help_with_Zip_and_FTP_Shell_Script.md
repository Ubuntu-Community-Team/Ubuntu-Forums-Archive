---
title: "Help with Zip and FTP Shell Script"
date: 2019-09-27
forum: General Help
---

### Post by shimabuku2 on 2019-09-27
I am trying to combine zip and ftp upload in one script but for some reason I can't get it to work. It zips properly but does not ftp, seems like it just ignores ftp. Any help would be greatly appreciated. Thanks!

```

#!/bin/sh
cd /home/user/test
zip -r test.zip *
FOLDER='/home/user/test'
ZIPS=$(ls $FOLDER)
for F in $zips ; do
  while [ -n '$(lsof | grep $F' ] ; do
  sleep 1
done
ftp -n <<EOF
open 192.168.1.66
user user pass
binary
put test.zip
EOF
done

```

---

### Post by Skaperen on 2019-09-27
it is typical for programs to read directly from the terminal for password input.  does it just pause forever when you run the script?

---

### Post by TheFu on 2019-09-27
Can I suggest using **rsync** over **ssh** with encryption and key-based authentication instead?  Security matters.  Plain FTP doesn't have much security and leaks credentials.  rsync is designed for this sort of stuff.

If you are stuck with plain ftp, you can use a ~/.netrc file to handle the terrible, non-encrypted, credential passing.  The manpage for it is **man netrc** .

---

### Post by shimabuku2 on 2019-09-27
> **Skaperen said:**
> it is typical for programs to read directly from the terminal for password input.  does it just pause forever when you run the script?

It doesn't pause or error out. It looks like it completes but I get no acknowledgement from the FTP server.

---

