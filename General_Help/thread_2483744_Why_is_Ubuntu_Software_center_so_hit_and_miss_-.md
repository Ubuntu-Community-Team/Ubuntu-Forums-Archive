---
title: "Why is Ubuntu Software center so hit and miss - ?"
date: 2023-02-07
forum: General Help
---

### Post by jonfisher on 2023-02-07
Why is Ubuntu Software center so hit and miss - ?

For example, right now I opened it, clicked the magnifying glass to search, and typed in "Gimp"

Well, it just searches and searches and twirls and twirls and nothing is ever returned.

And it's not just Gimp.  It seems like 50% or so of software that I search for, often that I know is in there like Gimp, never returns a result - ???

I often have to resort to Synaptic Software Package manager to get stuff...

---

### Post by monkeybrain20122 on 2023-02-07
It loads very slowly, so you have to wait for it to get populated. I believe it is due to the snap integration, since it loads much faster after purging it. It slows down again after installing the flatpak extension. The flatpak extension is not installed by default but snap's is.

If you just want to install standard packages (neither snaps nor flatpak) you should install synaptic, it is a gui front end for apt. It is much better than the app store though not so pretty

```
sudo apt install synaptic
```

Another thing is if app store promts you to update you always have to restart, it is PITA, So basically I disabled updates in the software store.

---

### Post by jonfisher on 2023-02-07
> **monkeybrain20122 said:**
> It loads very skowly, so you have to wait for it to get populated. I believe it is due to the snap integration, since it loads much faster after purging it. It slows down again after installing the flatpak extension. The flatpak extension is not installed by default but snap's is.

I haven't installed flatpak extension on either of my computers.  However, both my computers (an HP desktop & HP laptop) will just search and search indefinitely and not find what I'm looking for.

?  hmmmmm

---

### Post by monkeybrain20122 on 2023-02-07
snap is installed by default so it is there unless you purge it yourself.

See my edit for more info

---

### Post by jonfisher on 2023-02-07
> **monkeybrain20122 said:**
> snap is installed by default so it is there unless you purge it yourself.

See my edit for more info

This Synaptic you told me how to install, that's the same as Synaptic Package Manager that I already installed, right ?

---

### Post by monkeybrain20122 on 2023-02-07
> **jonfisher said:**
> This Synaptic you told me how to install, that's the same as Synaptic Package Manager that I already installed, right ?

yes. It is a lot better to use synaptic to install packages unless you want snap or flatpak. I believe you can do it much faster with command line than with the sofware store. Since I don't use snap you will have to either google or ask someone else  (for flatpak is like flatpak search gimp, then it shows you a bunch of options, then flatpak install /name/of/gimp/package, though I don't recommend gimp for either snap or flatpak because the sandboxing prevents installations of plugins, so apt or synaptic is your way to go)

---

### Post by Tadaen_Sylvermane on 2023-02-10
Flatpak search suffers from randomly not finding stuff as well, at least for me. In my case I wanted PyCharm and didn't want to use the snap. ```
flatpak search pycharm
``` just sits there, never returns anything found. But if I go to flathub I can find it as soon as I hit the search. A little annoying. One would think it would be consistent.

---

### Post by monkeybrain20122 on 2023-02-10
> **Tadaen_Sylvermane said:**
> Flatpak search suffers from randomly not finding stuff as well, at least for me. In my case I wanted PyCharm and didn't want to use the snap. ```
flatpak search pycharm
``` just sits there, never returns anything found. But if I go to flathub I can find it as soon as I hit the search. A little annoying. One would think it would be consistent.


It returns right the way here
```

flatpak search pycharm
Name       Description         Application ID            Version  Branch Remotes
PyCharm-C&#8230; The most intellige&#8230; &#8230;brains.PyCharm-Community 2022.3.2 stable flathub
Python 2.7 Extension for PyCh&#8230; &#8230;arm.Extensions.Python2-7 2.7.18   20.08  flathub
PyCharm-P&#8230; The most intellige&#8230; &#8230;ins.PyCharm-Professional 2022.3.2 stable flathub

```

so maybe you should check your internet connection.

---

### Post by Tadaen_Sylvermane on 2023-02-10
i can repeat the test over and over. everything else works fine. i won't jump to my internet connection being the problem if exactly one thing causes an issue that otherwise doesn't exist. flatpak search returns other stuff instantly as well. just not pycharm. i can't explain it.

For what it's worth I think I spend far to much time tinkering. I'm probably breaking stuff and not realizing it. For as long as I've been messing about with Linux stuff I've regularly had some type of problem that no one has ever heard of or can come up with a working solution for. For the longest time until I accepted that I do indeed try to fix what isn't broken I was seriously doubting this so called stability and things always working. Proved that when I had random bs stuff happening on Debian. If it happens on Debian then I'm at fault and that much I understand.
Same with Windows. I know people that use their machines daily without a single issue. Me... always something...

---

