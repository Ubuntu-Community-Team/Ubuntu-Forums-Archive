---
title: "XPS only opens when file is on main drive, permissions settings no affect"
date: 2014-10-30
forum: General Help
---

### Post by stevie6 on 2014-10-30
I'm dealing with .xps files and the documents viewer *can* open them, but says it doesn't have permission unless the file is on the main drive. Which is problematic due to  1) frequent use of thumb drives - that's alot of useless IMO copying and  2) I use another as my data drive (permissions given using Properties and checked in it's media reference - I see no problems).

---

### Post by cariboo on 2014-11-01
Check the file properties, they should look similar to this:

```
-rwxr-xr-x 1 cariboo cariboo 2882686 Oct 28 21:09 LU_Std_135103616_0114_0.pdf
```

the above permiision show that the pdf file is world readable (755). If you want the file readable only by your user (750) the permissions should look like this:

```
-rwxr-x--- 1 cariboo cariboo 2882686 Oct 28 21:09 LU_Std_135103616_0114_0.pdf
```

to set file permissions to world readable open a terminal and  use the following command:

```
chmod 755 *pdf
```

---

