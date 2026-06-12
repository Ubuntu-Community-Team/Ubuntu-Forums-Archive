---
title: "Synaptic and dependencies"
date: 2005-05-28
forum: General Help
---

### Post by kabanta on 2005-05-28
I want to install Quodlibet. When I select it in Synaptic, I get an error:

  "Depends: python (<2.4) but 2.4.1-0ubuntu2 is to be installed"

(Nevermind that python 2.4.1-0ubuntu2 is already installed, not "to be installed.") 

Two questions:

[list]
[*]any suggestions for a workaround?
[*]is there any way to see which INSTALLED packages depend on a
  package? (Synaptic seems to allow only the option of displaying ALL
  dependent packages.)
[/list]

---

### Post by Xian on 2005-05-28
[QUOTE=kabanta]is there any way to see which INSTALLED packages depend on a
  package? [/QUOTE]
Sure, just open aptitude (sudo aptitude) in a terminal and it will list the installed deps of any package.

---

