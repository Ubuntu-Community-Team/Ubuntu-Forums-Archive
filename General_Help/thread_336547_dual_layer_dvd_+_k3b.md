---
title: "dual layer dvd + k3b"
date: 2007-01-11
forum: General Help
---

### Post by Choad on 2007-01-11
my dvd's are DVD +R DL RW dual layer rewriteable beasts. k3b is saying i only have ~4 gig of space to use tho. i was under the impression that k3b was the way to go with dual layer dvd's.... how can i get to use all the space on them?

---

### Post by Choad on 2007-01-12
bump

---

### Post by goonies on 2007-01-15
this is why im still on windows, the lack of dual layer support on linux

---

### Post by Choad on 2007-01-16
> **goonies said:**
> this is why im still on windows, the lack of dual layer support on linux
well... for some bizzareo reason, i burned 7 gig to a dual layer dvd the other day just using the nautilus dvd burner

perfecto!

---

### Post by goonies on 2007-01-17
I need a program that can set custom layer breaks

---

### Post by goonies on 2007-02-04
imgburn + wine = :KS

---

### Post by g8m on 2007-02-05
k3b is just a frontend for burning. The actual tool is growisofs

growisofs -Z /dev/hdc -dvd-video dvd-folder. 

And this tool uses mkisofs to generate the dvd format

			Executing 'mkisofs -dvd-video mnt | builtin_dd of=/dev/hdc obs=32k seek=0'
			INFO:   ISO-8859-1 character encoding detected by locale settings.
				Assuming ISO-8859-1 encoded filenames on source filesystem,
				use -input-charset to override.


You could try to use growisofs in a terminal. Having said this, I burned dual layers with k3b with no problems what so ever.

---

