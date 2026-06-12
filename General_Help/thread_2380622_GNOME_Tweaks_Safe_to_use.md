---
title: "GNOME Tweaks? Safe to use?"
date: 2017-12-19
forum: General Help
---

### Post by sterator on 2017-12-19
I see that GNOME Tweaks is listed in the Ubuntu Software application. Can I infer that it has been vetted in terms of the adjustments offered in this little app are safe to use in Ubuntu 17.10?

There are a few items I'd like to modify but not at the expense of having a stable system.

Thoughts, please?

Thank you!

---

### Post by Frogs Hair on 2017-12-19
I've used gnome-tweak without any problems on many releases though I stick the basic extensions package available in the repository. Extensions offer additional functionality in the shell. Extensions will appear after reboot. ```
sudo apt install gnome-shell-extensions 
```

---

### Post by sterator on 2017-12-19
> **Frogs Hair said:**
> I've used gnome-tweak without any problems on many releases though I stick the basic extensions package available in the repository. Extensions offer additional functionality in the shell. Extensions will appear after reboot. ```
sudo apt install gnome-shell-extensions 
```

Thank you, Frogs Hair. Is it necessary to install the gnome-shell-extensions? Is that part of the entire process of installing and using GNOME Tweaks?

NM..answered my own question!

Thank you

---

### Post by ian-weisser on 2017-12-19
The developers of Gnome-Tweaks do not intend to compromise stability.

But the unexpected sometimes happens and people are very good at finding unforeseen ways to break their system.

In general, there are two kinds of options that are hidden by developers and exposed by GT and similar applications:

1) Options that are unpopular or confusing ("let's make everything sparkly!")
2) Options that are not fully tested or controversial ("let's put purple scroll bars in the middle of every window")

Now, I use GT also. And I've never had any problems either.
But that's different from promising a "stable system".

---

