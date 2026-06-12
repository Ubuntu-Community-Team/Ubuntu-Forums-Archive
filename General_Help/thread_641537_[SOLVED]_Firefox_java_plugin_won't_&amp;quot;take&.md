---
title: "[SOLVED] Firefox java plugin won't &amp;quot;take&amp;quot;"
date: 2007-12-15
forum: General Help
---

### Post by jackpetrilli on 2007-12-15
OS = Ubuntu 7.10

I've installed all the sun-java plugins available.  They simply won't take.  When I compare my desktop to my laptop firefox configuration (which works), it appears identical. I keep getting a message about missing plugins. When I click it, I get Java Runtime Environment available.  But when I try to install it through Firefox, it reports that it failed. 

Synaptic reports that all of the Java 6 plugins are installed, as is the JRE 1.4.2 etc.

about:plugins in firefox however, does not list any Java (like my laptop does).  

The GCJ controller is no good for me, as it fails to execute the main web site I need to have working.  I need the libjavaplugin_oji.so to be controlling my java plugin (like it does in the laptop).

I tried the link command listed - no effect - I get a "file already exists" msg.

I've uninstalled and re-installed java - no effect.

I've uninstalled and re-insalled firefox - no effect.  (The damn system remembers the configuration files, even though I told it to completely remove the configuration files.  After re-install, up came my all of my previous settings.  My FEBE backup was a waste of time.  Didn't need it!)

Maybe I need to adjust my userCHROME.CSS?  Does it even exist in Linux Firefox?

- Jack

---

### Post by rsambuca on 2007-12-15
32bit or 64bit OS?

Also, make sure you remove the gcj java too.

---

### Post by jackpetrilli on 2007-12-15
> **rsambuca said:**
> 32bit or 64bit OS?

Also, make sure you remove the gcj java too.

32 bit.  And yes, I've already removed all instances of gcj java (which, I think, originally created my problem.)

The plugins are there.  Firefox just won't link to them for some strange reason.

- Jack

---

### Post by jackpetrilli on 2007-12-15
My problem was solved by following the instructions given at the Sun Java site for a "manual install."  I had to change all Mozilla references to those of Firefox, and had to do quite a bit of directory inspecting to get the right ones, but it finally worked.

- Jack

---

