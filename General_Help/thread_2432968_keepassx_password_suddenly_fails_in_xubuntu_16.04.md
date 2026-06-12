---
title: "keepassx password suddenly fails in xubuntu 16.04"
date: 2019-12-11
forum: General Help
---

### Post by rosk333 on 2019-12-11
I have used keepassx for years with great success. Yesterday on my xubuntu 16.0.4 pc keepassx (2.0.2) suddenly quit accepting the database password.  The database file is still good, it can be opened using its password on a Xubuntu 18.04 laptop. On Xubuntu 16.04 it fails. I installed keepassx 2.0.3 - same problem. Even if I create a NEW database, save it, close it and attempt to open it again, it will not accept its password.
Has some encryption function been changed recently in 16.04?
Any suggestions as to what to try next?

---

### Post by rosk333 on 2019-12-12
Solved.
This problem was created by an entry in the line "Key File:" which appears in the first KeePassX window, below the "Password:" line.
The "Key File" referred to here is NOT the file that contains all your stored passwords (keys). That is called the Database File.
A "Key File" is some local file that can be used in conjunction with your KeyPassX Password to lock access to the Database file. 
The idea seems to be that if someone managed to steal a copy of your Database file AND your KeyPassX Password they still could
not access the Database entries if they had not managed to also steal the correct "Key File".

I have never willingly used a "Key File", preferring instead to use a secure memorized KeyPassX Password.

If, like me, you only use a secure memorized KeyPassX Password then to re-access your database NEVER have anything in the
"Key File" line. Also (probably) never set either of the buttons to the left of the "Key File:" or "Password:" lines.

The name and path to the Database file you wish to open should (confusingly!) appear under the line 'Enter Master Key' (which
in this case means the KeyPassX Password.)

If you have multiple tabs appearing above this line, remove the one(s) referring to databases you do not wish to open.

If after cleaning up all these items the database still cannot be opened, close KeePassX and re-open it. Check that only the one
correct database file is indicated and then enter only the Password:.

---

### Post by mailc on 2020-01-13
KeeepassXC  v KeepassX

Additional features of KeepassXC   compared to KeePassX:


-  Auto-Type on all three major platforms (Linux, Windows, macOS)
-  Twofish encryption
-  YubiKey challenge-response support
- TOTP generation
-  CSV import

Any user should consider using all credentials available: 
-  Password
-- Key File
-- Hardware Key  i.e Yubikey

---

