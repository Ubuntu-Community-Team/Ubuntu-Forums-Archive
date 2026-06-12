---
title: "How to add repository for openmovieeditor"
date: 2008-04-21
forum: General Help
---

### Post by anagnost68 on 2008-04-21
Hi,

I'd like to install openmovieeditor for feisty but I can't find a repository that has it and I'm not having much success finding a list of repositories or instructions on adding third party repositories.  

Does anyone know where openmovieeditor is and can give some tips on setting up the repository??

Thanks!

---

### Post by Achtung on 2008-04-22
For gusty, it's in the universe repository. Not sure about feisty, but you can always install from source, which can be downloaded on the project's website.

To add a third party repo, click system/administration/software sources and in the "Third-party software" tab, click "add". This will open a dialog in which all you have to do is enter the APT line of the repo that you want to add as source, e.g. "deb [http://adress.here.com/](http://adress.here.com/) distro comment".

---

