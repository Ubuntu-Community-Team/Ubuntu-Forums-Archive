---
title: "TEXINPUTS in home directory"
date: 2008-03-23
forum: General Help
---

### Post by evillan on 2008-03-23
As described in [https://help.ubuntu.com/community/LaTeX#head-ade5f8274ba80779fb5df55e02097aa143d130c7](https://help.ubuntu.com/community/LaTeX#head-ade5f8274ba80779fb5df55e02097aa143d130c7), I created a directory to place my locally installed LaTeX packages in /home/username/packages. Then I changed TEXINPUTS ("export TEXINPUTS=~/packages/:" in bash) so TeXlive will be able to find it. 

This worked fine.

However, I wan't to make sub directories, for example /home/username/packages/packagename, where files related to "packagename" are placed. But then I have to change TEXINPUTS, because the sub directories are not included already. So I wan't to modify TEXINPUTS so it includes all sub dirs without having to manually specify this for every package?
How is this achieved?

Thank you.

---

