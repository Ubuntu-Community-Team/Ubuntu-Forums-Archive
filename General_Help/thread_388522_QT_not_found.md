---
title: "QT not found"
date: 2007-03-19
forum: General Help
---

### Post by NTITech on 2007-03-19
```
checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!
```

That's the error I get when I try to run './configure' on a package that uses QT.  I have installed both QT3 and QT4 and both dev packages.  Why am I getting that error?

---

### Post by IcemanV9 on 2007-03-19
Does it show up in your $PATH for Qt??

```
echo $PATH
```

---

### Post by NTITech on 2007-03-19
```
nticompass@nticompass-laptop:~$ echo $PATH
/opt/mono-1.2.3.1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

---

### Post by SBFC on 2007-03-19
Are the qt-dev packages installed? I usually see messages similar to that when the dev packages are missing.

---

### Post by NTITech on 2007-03-19
There's only 'libqt3-mt-dev' no 'libqt3-dev'.  But, I have 'libqt4-dev' installed.

---

### Post by SBFC on 2007-03-19
My apologies, I now notice you already stated you had the dev packages installed.

What application are you trying to configure?

---

### Post by NTITech on 2007-03-19
I get this error on every QT-built package I try to configure.  Anyway, I am trying to configure Kfstab.

---

### Post by Jucato on 2007-03-19
1. Make sure you have libqt3-mt-dev installed
2. Do this only If it still complains, try setting QTDIR before running configure:

```
export QTDIR=/usr/lib/qt3
```
(presuming it's a Qt 3 app)

---

### Post by NTITech on 2007-03-19
WTF?  Why am I still getting QT not found?

---

### Post by NTITech on 2007-03-20
*bump, I tried everything and I still get "QT NOT FOUND"  WHAT IS WRONG?

---

### Post by ardath on 2007-05-03
NTITech,
try
```

export QTDIR=/usr/share/qt3
```
and then ./configure again. works in my case.

---

