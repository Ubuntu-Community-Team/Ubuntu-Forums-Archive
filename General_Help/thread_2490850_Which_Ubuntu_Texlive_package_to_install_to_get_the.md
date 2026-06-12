---
title: "Which Ubuntu Texlive package to install to get the Latex package isodoc ?"
date: 2023-09-18
forum: General Help
---

### Post by GwibberFooey on 2023-09-18
Hello!

Which Ubuntu Texlive package to install to get the Latex package isodoc ? 

For the record, I have previously attempted to the utility at  [https://packages.ubuntu.com/search?keywords=search](https://packages.ubuntu.com/search?keywords=search) , but I got poor results. More specifically, I searched the terms "texlive" "isodoc" and "texlive-isodoc", but in all cases it returned zero results.

See also The website from tex.stackexchange.com :  [https://tex.stackexchange.com/questions/470453/how-to-run-tlmgr-in-ubuntu](https://tex.stackexchange.com/questions/470453/how-to-run-tlmgr-in-ubuntu)

Any help would be very much appreciated!

---

### Post by deadflowr on 2023-09-18
Look at the texlive-latex-extra package.
Should contain the isodoc packaging you want.

---

### Post by GwibberFooey on 2023-09-18
I refined the search configuration at [https://packages.ubuntu.com/](https://packages.ubuntu.com/) which appears to return successful results. By toggling the option "display   packages that contain files whose names contain the keyword", the search engine seems to have a significantly wider breadth of scope.  As such, I see the package names "texlive-latex-extra-doc" and "texlive-latex-extra" . I am confident that one or both of them is sufficient.

---

