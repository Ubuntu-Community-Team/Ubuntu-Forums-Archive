---
title: "The 'cs' command"
date: 2007-04-01
forum: General Help
---

### Post by elreteipos on 2007-04-01
What can you do with 'cs'? How can I install it?

---

### Post by kidders on 2007-04-01
Hi there,

What is 'cs'?

---

### Post by elreteipos on 2007-04-02
That's what I want to find out. I need it to [build KDE4](http://techbase.kde.org/Getting_Started/Build/KDE4).

---

### Post by kidders on 2007-04-02
"cs" and "cb" appear to be scripts provided by the KDE devs to locate _s_ource (and presumably _b_uild or _b_inary) directories. They are not Linux utilities, which is probably why the URL you mentioned advises that they aren't typos.

---

### Post by elreteipos on 2007-04-02
I must have overlooked something then. But where can I download these scripts? I don't see a download link.

---

### Post by kidders on 2007-04-02
Hey again,

I took a closer look, and found the **cs** and **cb** function definitions. (They're functions, rather than scripts.)

```
function cs {
	# Make sure source directory exists.
	mkdir -p $KDE_SRC
 
	# command line argument
	if test -n "$1"; then
		cd $KDE_SRC/$1
	else
		# substitue build dir with src dir
		dest=`pwd | sed -e s,$KDE_BUILD,$KDE_SRC,`
		if [ $dest = `pwd` ]; then
		cd $KDE_SRC
		else
		cd $dest
		fi
	fi

}
```

```

function cb {
	# Make sure build directory exists.
	mkdir -p $KDE_BUILD
 
	# command line argument
	if test -n "$1"; then
		cd $KDE_BUILD/$1
		return
	fi
	# substitue src dir with build dir
	dest=`pwd | sed -e s,$KDE_SRC,$KDE_BUILD,`
	if test ! -d $dest; then
		# build directory does not exist, create
		mkdir -p $dest
	fi
	cd $dest
}
```

---

### Post by elreteipos on 2007-04-02
It appears that I had already put them in .bashrc and I just forgot to do *source .bashrc*. How stupid.

---

### Post by kidders on 2007-04-02
> **elreteipos said:**
> It appears that I had already put them in .bashrc and I just forgot to do *source .bashrc*. How stupid.

Hehe... easily done. Good to hear you're back in business though. :-)

---

