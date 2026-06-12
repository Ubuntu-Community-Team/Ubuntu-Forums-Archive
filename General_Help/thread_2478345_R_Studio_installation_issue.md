---
title: "R Studio installation issue"
date: 2022-08-23
forum: General Help
---

### Post by alfredohuerta on 2022-08-23
Hello,
I am having this issue when I try to install R studio.
Any ideas on how to fix the dependencies?

(base) alfredo@alfredo-hpelitebook725g4:~/Downloads$ sudo dpkg -i rstudio-2022.07.1-554-amd64.deb
(Reading database ... 416969 files and directories currently installed.)
Preparing to unpack rstudio-2022.07.1-554-amd64.deb ...
Unpacking rstudio (2022.07.1+554) over (2022.02.1+461) ...
dpkg: dependency problems prevent configuration of rstudio:
 rstudio depends on libssl1.0.0 | libssl1.0.2 | libssl1.1; however:
  Package libssl1.0.0 is not installed.
  Package libssl1.0.2 is not installed.
  Package libssl1.1 is not installed.
 rstudio depends on libclang-dev; however:
  Package libclang-dev is not installed.


dpkg: error processing package rstudio (--install):
 dependency problems - leaving unconfigured
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for shared-mime-info (2.1-2) ...
Errors were encountered while processing:
 rstudio

---

