---
title: "Missing libXft.so.1"
date: 2007-11-22
forum: General Help
---

### Post by michaelsharman on 2007-11-22
Hi guys,

I'm running Ubuntu 7.10 and want to install DBDesigner4 to do some database ERD's. The problem is that I don't have libXft.so.1 and can't find it anywhere.

1. Does anyone know where I can get this?
2. Does anyone recommend a good database diagramming tool to use for MySQL 5?

Thanks

Michael

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-23
Hi, 

> 
1. Does anyone know where I can get this?

First you need to install libxft2:
```

sudo apt-get install libxft2

```

Later, make link to libXft.so:
```

sudo ln -s /usr/lib/libXft.so.2.1.2 /usr/lib/libXft.so.1

```

> 
2. Does anyone recommend a good database diagramming tool to use for MySQL 5?

Can't help you with this, I'm searching this as well. BTW, have you tried "Dia Diagram Editor" ?

---

### Post by abracadaver on 2008-02-13
No, this doesn't work.  I get some qt undefined symbol error.  I installed libxft1 and it work perfectly.

sudo apt-get install libxft1

-Shawn

> **Milk & Toast & Honey said:**
> Hi, 


First you need to install libxft2:
```

sudo apt-get install libxft2

```

Later, make link to libXft.so:
```

sudo ln -s /usr/lib/libXft.so.2.1.2 /usr/lib/libXft.so.1

```


Can't help you with this, I'm searching this as well. BTW, have you tried "Dia Diagram Editor" ?

---

