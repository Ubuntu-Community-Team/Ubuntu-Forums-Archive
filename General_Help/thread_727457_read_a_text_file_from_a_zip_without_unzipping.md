---
title: "read a text file from a zip without unzipping"
date: 2008-03-17
forum: General Help
---

### Post by Joel Duckworth on 2008-03-17
Hi guys,

I know that the **less** command supports reading ***.gz** text files natively in the command line. The problem is we've got an application which generates **zip** files of the daily log. Is there any tool that will let us read the text file inside the zip without having to extract it first?

It will have to be a command line tool because it's on a server edition installation.

---

### Post by kerry_s on 2008-03-17
use " mc " it can read archives without extracting. i know it works on zips.
sudo apt-get install mc  <-if you don't have it already

mc  <-to launch

---

