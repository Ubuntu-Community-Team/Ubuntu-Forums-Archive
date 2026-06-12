---
title: "Packages, distributions, architectures"
date: 2008-06-24
forum: General Help
---

### Post by Excalibre on 2008-06-24
If I find a package for an app but want to install it on a different version of Ubuntu than intended, is that possible? How much are things likely to break? I'm asking because I'd like to try [gpicview](http://www.getdeb.net/search.php?keywords=gpicview) but as the link indicates, I can't find a package for Hardy; is it worth trying to use a Gutsy package, or am I stuck trying to compile from a source tarball (something that I've never had much success with)? I'm interested in general responses here because I don't really know much about how packages work beyond "you type the name of the package into Synaptic".

---

### Post by rampageoberon on 2008-06-24
you can install gpicview straight from the repositories in hardy too using synaptic or the following comamnd

```
sudo aptitude install gpicview
```

---

### Post by Taxman415a on 2008-06-24
Generally yes, it's possible, but no guarantees. You probably  shouldn't have much trouble installing just one release away. But if you're installing something from another source that's not in the repositories that's a bit of a risk anyway so caveat emptor in any case. For the package you mention in particular I find the installed by default gthumb image viewer works really well despite being a little slow to initially load. Clicking through the images in full screen mode is really fast and easy once you look at the commands.

---

### Post by Excalibre on 2008-06-24
> **rampageoberon said:**
> you can install gpicview straight from the repositories in hardy too using synaptic or the following comamnd

```
sudo aptitude install gpicview
```
*smacks forehead*

Uh, oops, yeah, seems like I probably should have looked there.

---

