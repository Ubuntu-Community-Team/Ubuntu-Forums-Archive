---
title: "nautilus won't start - symbol lookup error"
date: 2008-02-12
forum: General Help
---

### Post by miatawnt2b on 2008-02-12
My desktop seems to be all fouled up since nautilus refuses to start.  If I attempt to launch nautilus from a terminal I get the following error.

Initializing gnome-mount extension
nautilus: symbol lookup error: /usr/lib/nautilus/extensions-1.0/libnautilus-burn-extension.so: undefined symbol: nautilus_location_widget_provider_get_type

I have attempted to reinstall nautilus, nautilus-data, nautilus-cd-burner, nautilus burn packages, nautilus-extentions, and all the libgnomevfs stuff.   Still nautilus won't start.

Please help.

-J

---

### Post by apetresc on 2008-02-12
Do you have a package installed called ```
libnautilus-extension1
```  ?

---

### Post by miatawnt2b on 2008-02-12
> **AdrianP said:**
> Do you have a package installed called ```
libnautilus-extension1
```  ?

Sure do.  1:2.20.0-0ubuntu7

-J

---

### Post by apetresc on 2008-02-12
> **miatawnt2b said:**
> Sure do.  1:2.20.0-0ubuntu7
Is it one of the packages you tried to uninstall/reinstall originally? You didn't mention it  in your list.
If not, try to do so.

The problem is with the linker, it's trying to access a symbol in that library that has been (re?)moved.

---

### Post by miatawnt2b on 2008-02-12
> **AdrianP said:**
> Is it one of the packages you tried to uninstall/reinstall originally? You didn't mention it  in your list.
If not, try to do so.

The problem is with the linker, it's trying to access a symbol in that library that has been (re?)moved.

Thanks for the help so far...
 I'm not sure if I tried to re-install that package initially, but I attempted a reinstall just now, and I get the same error.

-J

---

### Post by miatawnt2b on 2008-02-12
> **miatawnt2b said:**
> Thanks for the help so far...
 I'm not sure if I tried to re-install that package initially, but I attempted a reinstall just now, and I get the same error.

-J

and I did check, the libnautilus-burn-extension.so file is there with like permissions as the other files in that dir.  

This is truly strange. It was working earlier this morning, before the daily ubuntu updates. (not even sure what those were today)

-J

---

