---
title: "Synconisation between two workstations and an server (on the internet)"
date: 2006-12-10
forum: General Help
---

### Post by krage on 2006-12-10
I have two workstations that run kubuntu, and I have access to an server on the thats placed in an serverrom somewhere.

One of the computers is always connected to the internet, but the other one (an laptop) is not, because of thise I would like my computers to syncronise the files in my ~/documents up to the server once every day, when they start up, and when I ask for it.

I would likte them to check if a file have a newer version on the local machine or on the server and then make a copy if one of them have a newer version. If a file dos not exist one of the places i would like it to copy the file over, the same if I make an new folder called ~/documents/foo then they should do the same with thise folder.

I would be wery happy if somebody could help me with thise :-)

(I have SSH access to the server)

---

### Post by dbw on 2006-12-10
Have you looked into using [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/")?  It seems to do what you want, and is available in the repos ( i.e. Aptitude/Synaptic).

---

