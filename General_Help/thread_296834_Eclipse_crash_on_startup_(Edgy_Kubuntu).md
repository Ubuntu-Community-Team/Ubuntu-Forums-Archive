---
title: "Eclipse crash on startup (Edgy Kubuntu)"
date: 2006-11-10
forum: General Help
---

### Post by Hikaru79 on 2006-11-10
Whenever I try to start up Eclipse, either with or without sudo, it gives this and just crashes:
```
adrian@navi:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...found
kdialog: Unknown option '--warning'.
kdialog: Use --help to get a list of available command line options.
```
The last JVM is found, so I doubt it is a Java-related problem. Perhaps something to do with kdialog crashing because its unable to open one of Eclipse's things?

Any ideas?

---

### Post by boban on 2006-11-10
(I'm making a guess :) )

You have installed from repositories, right? And you probably don't have mozilla/firefox installed...

I think that there is solution for you... Edit file /usr/bin/eclipse (with root rights). Find there:

```

# Set path for the Mozilla SWT binding
MOZILLA_FIVE_HOME=${MOZILLA_FIVE_HOME%*/}
if [ -n "$MOZILLA_FIVE_HOME" -a -e $MOZILLA_FIVE_HOME/libgtkembedmoz.so ]; then
    :
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/xulrunner/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/firefox
elif [ -e /usr/lib/mozilla-firefox/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla-firefox
elif [ -e /usr/lib/mozilla/libgtkembedmoz.so ]; then
    export MOZILLA_FIVE_HOME=/usr/lib/mozilla
else
    $DIALOG \
        --warning \
        --title="Integrated browser support not working" \
        --text="This Eclipse build doesn't have support for the integrated browser."
    [ $? -eq 0 ] || exit 1
fi

```

And remove this part:

```

else
    $DIALOG \
        --warning \
        --title="Integrated browser support not working" \
        --text="This Eclipse build doesn't have support for the integrated browser."
    [ $? -eq 0 ] || exit 1

```

I don't know if it is a proper way to solve your problem, but it should help...

---

### Post by boban on 2006-11-10
Hmm... and another thing... you could just try starting eclipse with:

```

/usr/lib/eclipse/eclipse 

```

---

### Post by littlespy on 2006-11-10
I had the same problem and neither of these 2 solutions have fixed it.  There is a bug report filed for this problem and a solution but a new eclipse package has not been added to the repository.

---

### Post by Hikaru79 on 2006-11-15
Thanks, guys! Both of those solutions actually worked flawlessly. :)

---

### Post by cosine7 on 2006-11-18
```
sudo /usr/lib/eclipse/eclipse

```

Try this

---

### Post by Hikaru79 on 2006-11-20
> **cosine7 said:**
> ```
sudo /usr/lib/eclipse/eclipse

```
 
Try this
Yes, as I've already said, that works :P Though the 'sudo' is not needed.

---

### Post by cosine7 on 2006-11-20
> **Hikaru79 said:**
> Yes, as I've already said, that works :P Though the 'sudo' is not needed.

Sorry i should have quoted you last time. :-D  It would not work on my system without the ```
sudo
```

---

