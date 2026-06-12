---
title: "quick vmware question(removing virtual drive)"
date: 2007-10-12
forum: General Help
---

### Post by d_xtremw on 2007-10-12
ok heres my problem, i originally had vmware 1.0.3 and created a virtual drive of about 10gigs. then i had to uninstall v1.0.3 and instal 1.0.4. but the virtual drive i created still exists somewhere and its making it impossible to create new virtual drives with 1.0.4 and slowing down my computer. does anyone know where this drive would be located and how i can delete it??

---

### Post by ruibernardo on 2007-10-12
Hi d_xtremw,

I think that by default vmware creates your vm in /var/lib/vmware/VirtualMachines/ or something like that (i'm using qemu now, so I can't confirm it). 

If you didn't delete (as in "delete from disk", not just delete from the menu) your previous vm is still there, you just have to open that vm again and run it.

If you really want to delete it from disk, open it (select it from the open menu) and then right-click on it and select "delete from disk". This is the right way of deleting vm.

Another option, is to rm -rf the directory of that vm (with sudo), but then vmware will still have it on your menu. Then you can delete from the menu, but why bother with all this, if you can do it the "right way" with just one right-click?

---

### Post by d_xtremw on 2007-10-13
thank you very much. i had 2 different vmware installation files so it just took me sum time to figure ut which 1 was which since i installed the same version of XP on both.  thanx again

---

### Post by d_xtremw on 2007-10-13
just another quick question, does anyone know how to transfer files from the guest OS to the host OS and back. because i hav alot of files from Ubuntu which i want to work with in XP and vice versa but even though it copies text across the 2, it doesn't copy files. any help would be appreciated

---

