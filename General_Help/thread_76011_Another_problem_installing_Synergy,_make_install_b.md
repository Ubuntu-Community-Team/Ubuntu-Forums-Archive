---
title: "Another problem installing Synergy, make install breaks"
date: 2005-10-14
forum: General Help
---

### Post by ptepper on 2005-10-14
Hi, 

I went through a dozen forums trying to get Synergy running in 5.10. I know there's a version for hoary, but it won't work with my mac and the synergy rpm says it's missing some libs, so I'm trying to build from source. 

I get up to the 'make install' point (after getting libxtst-dev installed). Now I get through configure fine but it breaks during make install.  
 
The errors seem to be coming from CXWindowsClipboard.cpp, starting as follows: 

```

In file included from CXWindowsClipboard.cpp:15: 
CXWindowsClipboard.h:24:3: error: #error X11 is required to build synergy 
In file included from CXWindowsClipboard.cpp:21: 
CXWindowsUtil.h:23:3: error: #error X11 is required to build synergy 
CXWindowsClipboard.h:38: error: expected `)' before ‘*’ token 

```

It continues this way with error messages, which look syntactic, on many lines up to 1485, where it ends with: 
 
```

CXWindowsClipboard.cpp:592: warning: control reaches end of non-void function 
make[2]: *** [CXWindowsClipboard.o] Error 1 
make[2]: Leaving directory `/.../synergy-1.2.4/lib/platform' 
make[1]: *** [install-recursive] Error 1 
make[1]: Leaving directory `/.../synergy-1.2.4/lib' 
make: *** [install-recursive] Error 1 

```

Is the ubuntu install actually missing some part of X11 that this needs?
 
any suggestions on how to get the make install to finish? Didn't see anyplace for posting questions about other apps, but let me know if this is the wrong place to post this.
 
thnx

---

### Post by ptepper on 2005-10-15
Nevermind, the version in Synaptic now seems to be working fine with Mac.

---

### Post by spook on 2005-10-17
I have this problem with make as well. anyone know what the problem is?

Edit: nevermind. a slightly earlier version is available through synaptic.

---

### Post by winf3red on 2006-01-20
If anyone is still interested in building this from source, you simply need to set your -x-includes and -x-libraries switches when you run ./configure.  
For me, and probably most people with the standard install, these pointed to /usr/includes and /usr/lib respectively.

Enjoy

---

### Post by reformist on 2006-04-01
Thanks winf3red! Great tip.

I've posted a full writeup of building it from source [here]("http://philisoft.com/blog/install-latest-synergy-on-ubuntu/").

---

### Post by skeltoac on 2006-05-07
I had to make a small change to get it to work:

/usr/include

(n.b. it's not plural)

Thanks for the xtst tip!! :)

---

### Post by mael on 2006-05-16
even with this parameters i couldn't compile synergy on hoary
but it worked even without the paramteres on breezy - and the binaries created there are woking on hoary :)

---

