---
title: "Multiple Deb Packages at Once"
date: 2008-06-20
forum: General Help
---

### Post by phildaman46 on 2008-06-20
Can you install a whole bunch of deb packages all at once without having to use a terminal?

---

### Post by sdennie on 2008-06-20
I don't think so (but, I could be wrong).  I just selected a bunch of .deb files, right clicked and said "Open with GDebi".  I don't recommend doing that.  Is there a reason you can't use the command line to do this?  If, for example, you have a directory that is full of .deb files that you want to install you can simply say:

```

sudo dpkg -i *.deb

```

---

### Post by rolandixor on 2008-06-20
vor is right.
maybe you could use a CD RW with APT on CD but that's overkill... lol

---

### Post by phildaman46 on 2008-06-20
> **vor said:**
> I don't think so (but, I could be wrong).  I just selected a bunch of .deb files, right clicked and said "Open with GDebi".  I don't recommend doing that.  Is there a reason you can't use the command line to do this?  If, for example, you have a directory that is full of .deb files that you want to install you can simply say:

```

sudo dpkg -i *.deb

```

I was just wondering if it was possible. I have no problem using the terminal. If you selected a bunch of deb files and opened them with GDebi, would that load a bunch of GDebi package managers all at once? I wouldn't like that method.

---

### Post by sdennie on 2008-06-20
> **phildaman46 said:**
> If you selected a bunch of deb files and opened them with GDebi, would that load a bunch of GDebi package managers all at once? I wouldn't like that method.

That's exactly what it does, which is why I said I don't recommend trying it.  ;)

---

### Post by rolandixor on 2008-06-21
Someone needs to fix that. Maybe we could start a new project called Multidebi? lol.

---

### Post by ShodanjoDM on 2008-06-21
You can use Synaptic for that: File > Add Downloaded Packages.

---

### Post by rolandixor on 2008-06-21
sure. but you can use it to install multiple files from a local folder so easily.

---

