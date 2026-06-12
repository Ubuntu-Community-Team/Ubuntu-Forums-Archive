---
title: "Dependency problems"
date: 2006-12-13
forum: General Help
---

### Post by hareti on 2006-12-13
Hi there,

I'm having some problems installing Hugin, a image stitching program. It requires libpano version 2.8 or greater but the version that synaptic has is only 2.7 so Hugin won't compile. I found libpano 2.8 .deb package on the Debian site so I have downloaded this but when I try to install it simply by double clicking on it I get a dependency error. It says it needs libc6 and can't find it but libc6 is definitely listed in synaptic as installed. 

How can I get around this?

Thanks

---

### Post by ciscosurfer on 2006-12-13
For the most part, the Debian repos do not mix well with Ubuntu.  Ubuntu is based on Debian, yes, but the repos for Debian are made specifically for their releases.

---

### Post by hareti on 2006-12-13
OK I see. So if I need a newer version of software that is in the Ubuntu repos, the only way forward is to compile from the latest source?

Now, suppose I have program A that is installed from a package and depends on library B also installed from a package. Now I want to compile a new program C that requires a newer version of library B that is not available in the repos. If I uninstall the library using the package manager and compile and install the newer version from source, that solves the problem for the new program C but breaks dependencies for program A. Hypothetical question - I was just wondering.

Thanks for your help

---

### Post by ciscosurfer on 2006-12-13
I looking for a particular thread right now that should help you out with this hypothetical...I would startx explaining it here, but I'd probably massacre the bulk of the points made of this other thread.  I'll keep looking for it.  I remember it was in a thread made by one of the Forum Staff and it was a "Dapper or Edgy upgrade issues" thread and how to solve issues that came up during an upgrade.  I keep looking but feel free to search for it as well. :-)

---

### Post by hareti on 2006-12-13
Thanks Ciscosurfer,

I'm running Xubuntu 6.06. If i do a search for a prgram in Synaptic will it only return packages meant for that release, or all packages. i guess this is where the upgrading issues come from.

I see there is a note on the Xubuntu website about upgrading from Dapper to Edgy. I'm off to have a read...

---

### Post by ciscosurfer on 2006-12-14
> **hareti said:**
> Thanks Ciscosurfer,

I'm running Xubuntu 6.06. If i do a search for a prgram in Synaptic will it only return packages meant for that release, or all packages. i guess this is where the upgrading issues come from.

I see there is a note on the Xubuntu website about upgrading from Dapper to Edgy. I'm off to have a read...Still haven't found that link yet.

What appears in Synaptic is dependent on which repositories you have enabled in your sources.list

You can read more about enabling your extra repo here: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

How was that other link you found on the Xubuntu website?

---

