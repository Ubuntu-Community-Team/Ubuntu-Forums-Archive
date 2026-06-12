---
title: "Extremely slow printing of pdf file made from a powerpoint with background Edit"
date: 2017-06-01
forum: General Help
---

### Post by bopodelvalle on 2017-06-01
Hello all!

I've had this problems for years (Since Ubuntu 10.04. Now I'm using 16.04) and I decided now to write about it. I have a few files that come from Powerpoint and saved into PDF. Those files have a background with some patterns/vectors/whatever that make the printing extremely slow. Processing of each of this pages takes several minutes.


You can find the file here: [https://www.dropbox.com/s/6rzee0q3nszbpd5/PPT%20with%20background.pdf?dl=0](https://www.dropbox.com/s/6rzee0q3nszbpd5/PPT%20with%20background.pdf?dl=0)


Im using the following driver: HP Color LaserJet 9500 pcl3, hpcups 3.16.11. Using a Gutenprint driver seems to fix the issue. However. There are other several documents that have problems with Gutenprint, therefore, I would prefer to keep the HP driver and try with some different workaround.


The command I'm using to print is:

```
lp -d printer -o fit-to-page -o media=Letter -o number-up=4 -o page-border=none -o number-up-layout=btlr -o sides=two-sided-short-edge "/home/ubuntu/filename.pdf"

```


I hope we can find the bug. I've find several similar problems and no solution yet.


Thanks!

---

