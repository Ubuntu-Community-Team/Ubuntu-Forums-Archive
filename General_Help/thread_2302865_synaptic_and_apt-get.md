---
title: "synaptic and apt-get"
date: 2015-11-14
forum: General Help
---

### Post by carlos_silva2 on 2015-11-14
Are synaptic and apt-get using different lists of packages?

For example, package 'dgen' under synaptic is not found, but with apt-get there it is.

How many more packages are like this?

---

### Post by howefield on 2015-11-14
I'm guessing that it is finding it, you are just not seeing it :)

Are you using a 64 bit version of Ubuntu, I believe dgen is available only as 32 bit ?

So in synaptic try clicking on the Architecture button in the left hand pane

---

### Post by grahammechanical on 2015-11-14
Ubuntu Software Centre on Ubuntu amd64 has dgen:i386. As Howefield says, in Synaptic if we set Architecture to "all" or "arch:i386" we find dgen but not if Architecture is set to "arch:all" or "arch:amd64."

Each Ubuntu release/version has it own repositories that are closed when the release reaches its end of support date. But all Ubuntu products, including the other members of the Ubuntu family of distributions, are built from the packages in the same set of repositories. Not all repositories are enabled by default. The Partner repositories have to be enabled by the user. So, Ubuntu Software Centre may offer an application but not be able to install it as it is in the Partner repository which has yet to be enabled.

Regards.

---

### Post by carlos_silva2 on 2015-11-14
Thanks guys! That was exactly what happened, case closed ;-)

---

### Post by oldos2er on 2015-11-14
Please mark the Thread as 'Solved' under the Thread Tools menu, and thanks.

---

