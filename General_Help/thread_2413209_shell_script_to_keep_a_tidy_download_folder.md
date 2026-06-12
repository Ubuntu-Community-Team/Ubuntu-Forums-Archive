---
title: "shell script to keep a tidy download folder"
date: 2019-02-22
forum: General Help
---

### Post by mattdawolf on 2019-02-22
I have only ever written rudimentary shell scripts. I want a way to keep my main downlpad folder tidy after transmission and ktorrent move their finished downloads to it so I needn't have to keep manually moving and deleting things.

what is the best way to accomplish this in shell?

Premise: Download directory gets cluttered with subfolders, most of the time just having one file in it.

·       Go into ~/foo/downloads

o    

·       If dir has files of type A, B, C, D, E, F, mv types A, B, and C up to the parent directory. Then rm –Rf that folder with any files in it.

·       If dir has just one file in it, move it up to parent directory regardless of extension then remove that subdir.

·       If dir has files of type G, H, I in it, and filecount is greater than 5, mv that folder up to the parent directory.

·       If dir has files of type J, K, L in it, move the whole directory up one level

---

### Post by oldfred on 2019-02-23
The few bash scripts I created were from copying the history file commands I used into a text file with header for bash & edit out the sudo command.
You need to test your commands anyway.

---

