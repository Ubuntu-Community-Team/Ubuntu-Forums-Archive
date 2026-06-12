---
title: "permission denied"
date: 2007-02-19
forum: General Help
---

### Post by fouad167 on 2007-02-19
hi all,
i am kinda stuck at this and any help would be highly appreciated

i compiled subversion with --prefix=/root/usr/local and it is working well, the issue is that 
sudo -u apache /root/usr/local/bin/svn
gives permission denied even though i chmoded it to 755, i can't figure out what is going wrong

thanks a lot

foaud

---

### Post by taurus on 2007-02-19
Any reason why you have it set to --prefix=/root/usr/local instead of --prefix=/usr/local?  The path looks a little odd to me.

---

