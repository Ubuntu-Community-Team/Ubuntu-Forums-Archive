---
title: "Investigating patterns when performing operations on regular files in ext4"
date: 2020-09-29
forum: General Help
---

### Post by kseeniaa on 2020-09-29
[COLOR=#000000][FONT=Verdana]I am doing an assignment, but I was in doubt and do not know how to answer the last question.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Can anyone help me please.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Question 9. When performing steps 2, 11 for a 129 MB file, carefully study the result and answer the following questions:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]What differences can be noted in the logic of block allocation by extent?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]How can these differences be explained?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Is the logical order of the blocks in a file always the same as the physical order of their location on disk?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]What about the maximum extent size?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]What about the last extent size?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]step 2. In the ~ / dir1 / directory, create three 512-byte files with[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]with the prefixes a_, b_ and c_, and in the ~ / dir2 / directory there is a similar file with the prefix d_.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Use commands like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ yes aaa-512b- | tr -d "\ n" | dd bs = 1 count = 512> dir1 / a_512b[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ yes bbb-512b- | tr -d "\ n" | dd bs = 1 count = 512> dir1 / b_512b[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ yes ccc-512b- | tr -d "\ n" | dd bs = 1 count = 512> dir1 / c_512b[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ yes ddd-512b- | tr -d "\ n" | dd bs = 1 count = 512> dir2 / d_512b[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]step 11. Investigate the behavior of the file system for three cases:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]writing a file to the location of the remote file (i.e. with the name of the remote file);[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]writing a file over an existing one in the same directory;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]overwriting an existing file in another directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Use commands like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ cp ./dir1/a_512b ./dir1/b_512b[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ cp -f ./dir1/a_512b ./dir1/c_512b[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]user @ polygon: ~ $ cp -f ./dir1/a_512b ./dir2/d_512b[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks in advance.[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-29
We don't do home work here. It is against forum policy.

---

