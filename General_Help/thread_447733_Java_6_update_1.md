---
title: "Java 6 update 1"
date: 2007-05-18
forum: General Help
---

### Post by abruegl on 2007-05-18
I have Java 6, but I'm interested in why the Sun Java releases are so behind in Synaptic, it seems like months before the new packages are updated in there.

It just bothers me that with windows I just download an exe release from the official site and run it. And with Ubuntu I am always so behind with my updates :(

Why is this sooo slow to update? For instance I don't see Pidgin available either.

---

### Post by carlosqueso on 2007-05-18
Ubuntu releases a completely new set of packages every six months.  The last release was mid-april, although they probably froze it before then.   Between releases, they only release security updates, and some bugfixes.   There is a backports project, but they only release software that won't screw up the system, and libraries like Java have the potential to screw up the system if something's changed.  Same for pidgin, as other programs will still expect it to be called gaim.

---

### Post by abruegl on 2007-05-23
> **carlosqueso said:**
>  Between releases, they only release security updates, and some bugfixes.   ... they only release software that won't screw up the system, and libraries like Java have the potential to screw up the system if something's changed

I disagree.

Update releases for Java are just that, and a direct quote from Sun at [http://java.sun.com/javase/6/webnotes/ReleaseNotes.html:](http://java.sun.com/javase/6/webnotes/ReleaseNotes.html:)
"Update releases are bug fix releases and as such are not intended to add or delete functionality from the original 1.6.0 release"

I think it is bad practice then to not release the Java updates promptly, in fact on Windows, Java updates are automatically downloaded. Ubuntu should also support these updates through it's update manager.

---

