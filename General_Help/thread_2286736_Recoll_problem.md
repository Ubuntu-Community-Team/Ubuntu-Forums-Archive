---
title: "Recoll problem"
date: 2015-07-14
forum: General Help
---

### Post by Robbyx on 2015-07-14
Ubuntu 14.04 AMD 64

I can not get Recoll to work since upgrading my computer hardware and reinstalling Ubuntu.

I have reinstalled recoll from synaptic. How do I make these error messages go away?

```
robins@robins-desktop:~$ recollindex
:4:../utils/execmd.cpp:186:ExecCmd::startExec: (0|0) /usr/bin/ionice {-c} {3} {-p} {7539} 
:4:../utils/execmd.cpp:473:ExecCmd::wait: got status 0x0
:4:../rcldb/rcldb.cpp:610:Db::open: m_isopen 0 m_iswritable 0
:2:../rcldb/rcldb.cpp:689:Db::open: exception while opening [/home/robins/.recoll/xapiandb]: Cannot open tables at consistent revisions
:2:../index/indexer.cpp:58:ConfIndexer: error opening database /home/robins/.recoll/xapiandb : Cannot open tables at consistent revisions
Indexing failed
:4:../rcldb/rcldb.cpp:589:Db::~Db: isopen 0 m_iswritable 0
:4:../rcldb/rcldb.cpp:704:Db::i_close(1): m_isopen 0 m_iswritable 0
robins@robins-desktop:~$ 


```

---

### Post by dino99 on 2015-07-14
what are the xapiandb properties ?

note that some new bugs are opened  [https://bugs.launchpad.net/bugs/+bugs?field.searchtext=recoll&search=Search%20Bug%20Reports&field.scope=all&field.scope.target=&orderby=-date_last_updated&start=0](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=recoll&search=Search%20Bug%20Reports&field.scope=all&field.scope.target=&orderby=-date_last_updated&start=0)

---

### Post by Robbyx on 2015-07-14
Thanks for the reply. 

No problem with the properties. They are in my user name. I have completely uninstalled recoll and deleted  its index files and then reinstalled and am doing a fresh installation of recol. That has not shown any errors so far.

---

