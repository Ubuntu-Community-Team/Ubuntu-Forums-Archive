---
title: "adesklets dependency problem"
date: 2006-12-11
forum: General Help
---

### Post by Nycthbris on 2006-12-11
I'm sure there is probably a simple solution to this but I can seem to figure it out. When I try to install adesklets with:
```
sudo apt-get install adesklets
```
I get this:
```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
So I do an "apt-get -f install" with no packages and it returns me this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

Any help would be great! Thanks!

---

### Post by Nycthbris on 2006-12-11
Okay, I've figured out that I have a broken libfontconfig1 package. How do I fix such a thing? In synaptic if I choose to reinstall it, I am told I have to remove just about everything on my system. Is there any way around this?

---

### Post by nblit on 2006-12-25
I had the same problem and this is what is did:

1. open terminal and run sudo aptitude purge  fonconfig-config
2. result: 

Downgrade the following packages:
fontconfig-config [2.4.2-1 (now) -> 2.3.2-7ubuntu2 (edgy, edgy)]
Score is -40
Accept this solution? [Y/n/q/?] y <--select yes

3. Click 'Y' if prompted again

That did it for me

Ciao

---

### Post by amano on 2007-01-20
):P  Thanks. I ran into that problem myself, when trying to install some feisty packages to get totem 2.17.5 running.
That solved the program for me.

---

