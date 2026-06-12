---
title: "software center not working and update manager doesnt either"
date: 2013-05-11
forum: General Help
---

### Post by newbieroot on 2013-05-11
here is the error i get

Reading package lists... Error! E: Problem parsing dependency Depends E: Error occurred while processing tntdb-sqlite3 (NewVersion2) E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages E: The package lists or status file could not be parsed or opened.

---

### Post by ibjsb4 on 2013-05-11
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one line at a time):

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

Any questions? Just post back :)

---

### Post by newbieroot on 2013-05-11
thanks alot that worked

---

### Post by ibjsb4 on 2013-05-11
And welcome to the forums :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

