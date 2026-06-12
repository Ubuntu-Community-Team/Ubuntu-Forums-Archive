---
title: "Little problem with Greek characters"
date: 2008-07-09
forum: General Help
---

### Post by darkconcept on 2008-07-09
Hello to all.

Absolute beginner here...needed a way out of windows, so I decided to install ubuntu on my laptop, leave winxp on my desktop and maintain that duality until I feel comfortable to get completely rid of windows.

Anyway, in the meantime I needed a way to share my documents in the two computers and to be able to synchronize them. Therefore I  setup Samba on Ubuntu and made my documents shared. I logged in from Windows and I could see and copy files in the Ubuntu shared folder. So far so good.

I then tried to synchronize the two folders using a windows software program called Total Commander. Although the program accesses fine the linux share, it seems to have a problem with Greek-Named files. Assume for example the file &#945;&#946;&#947;.doc. Even if it exists in both of the folders being synchronized, the synchronizer will tell me that I need to copy &#945;&#946;&#947;.doc from the Linux document folder to the Windows document folder and vice versa. This means, that although the files are identical in content, attributes, and name, the synchronizer sees them as different. This problem did not appear when synchronizing files between two windows machines.

I am assuming something is wrong with the greek support of ubuntu although I did install the greek locale in addition to the english one.

Any tips would be greatly appreciated..

Cheers!
DC

---

### Post by simosx on 2008-07-21
It's actually a complication in Windows. They use the legacy 8-bit encoding windows-1253 which requires some additional configuration on Ubuntu's part.

---

