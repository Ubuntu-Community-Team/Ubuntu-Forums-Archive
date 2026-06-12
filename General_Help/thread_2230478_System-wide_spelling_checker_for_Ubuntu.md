---
title: "System-wide spelling checker for Ubuntu"
date: 2014-06-19
forum: General Help
---

### Post by blnl on 2014-06-19
Is there system-wide spelling check tool for Ubuntu?
If yes, how to install dictionaries for Dutch and Croatian languages?

---

### Post by grahammechanical on 2014-06-19
In System Settings>Language Support we can install languages and with the keyboard utility we can install different language keyboard layouts. Applications like Libreoffice have their own spell checker utilities and may require additional language spell checker add-ons.

---

### Post by Impavidus on 2014-06-19
Open the software centre or synaptic (or the terminal) and search for **aspell-hr**, **myspell-hr**, **aspell-nl** and/or **myspell-nl**, hr being croation and nl being dutch, of course. The aspell packages are for the aspell spell checker, the myspell packages for the hunspell spell checker (compatible with myspell, hence the name), which is used as a plugin in several applications like libreoffice and firefox. Both can also be used as stand-alone tools. People say the hunspell spell checker is better for languages with richer morphology, so for dutch it's supposed to be better. I don't know about croatian, as I don't speak it. It's better supported as plugin anyway.

---

### Post by blnl on 2014-06-19
> **grahammechanical said:**
> In System Settings>Language Support we can install languages and with the keyboard utility we can install different language keyboard layouts. Applications like Libreoffice have their own spell checker utilities and may require additional language spell checker add-ons.

No different language keyboard layouts, that is not what I need. My keyboard stays English USA.
Only the text in the documents and instant messaging must be checked for spelling errors.

---

### Post by blnl on 2014-06-19
> **Impavidus said:**
> Open the software centre or synaptic (or the terminal) and search for **aspell-hr**, **myspell-hr**, **aspell-nl** and/or **myspell-nl**, hr being croation and nl being dutch, of course. The aspell packages are for the aspell spell checker, the myspell packages for the hunspell spell checker (compatible with myspell, hence the name), which is used as a plugin in several applications like libreoffice and firefox. Both can also be used as stand-alone tools. People say the hunspell spell checker is better for languages with richer morphology, so for dutch it's supposed to be better. I don't know about croatian, as I don't speak it. It's better supported as plugin anyway.

In Fedora it is only hunspell that is used by all application (firefox, thunderbird, evolution, libreoffice, gedit, tomboy).

So in order to install hunspell in Ubuntu I need to search for myspell-*, all right.
Then I'll start installing myspell modules for NL and HR, and see how many applications do recognize it.

---

