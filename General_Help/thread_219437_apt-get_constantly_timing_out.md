---
title: "apt-get constantly timing out"
date: 2006-07-20
forum: General Help
---

### Post by dwinks on 2006-07-20
Whenever I use synaptic, apt-get, etc, it will stop downloading in the middle of a package, and doesn't resume unless I restart the apt-get.  I witnessed my connection downloading a 3gig file from the internet while doing an apt-get, and I am 100% certain that my connection is steady, as the download doesn't stop, only the apt-get does.

It says "Get:35 http://archive.ubuntu.com..." then on the next line it shows the progress of the package downloading.  It will just stop, and the download fails for no reason.

Luckily it uses wget, so it resumes from incomplete data, as downloading a 30mb package often takes 5-10 tries with it freezing every few % downloaded.

I've tried the US servers, the default ones, and even overseas ones with all the same effect.  There seems to be some bug in the programming, or in the default set-up for Dapper.

I am using a computer connected to a decent router connected to a solid cable modem connection.  Pretty standard I would think.

Any ideas on this would be certainly appreciated, as it is getting rather annoying =/

---

### Post by Christmas on 2006-07-20
I'm not sure but maybe you can try changing your repositories. Here's a link to a sources.list generator by country: [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic"). Enter your country two-letters code and you will be provided with a sources.list file for that country.

---

