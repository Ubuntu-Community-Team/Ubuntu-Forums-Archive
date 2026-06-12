---
title: "remove apt-key"
date: 2020-01-23
forum: General Help
---

### Post by jgw on 2020-01-23
I am trying to remove an apt-key   I did an apt-key list and here is the one I want to delete:

pub   rsa2048 2015-05-02 [SC]
      B6DA 722E 2E65 721A F54B  9396 6F75 6587 9798 C2FC
uid           [ unknown] Enpass Packaging Team <package@enpass.io>
sub   rsa2048 2015-05-02 [E]

My problem is that the command to delete one is "del keyid" so I need the keyid.  I am assuming that one of the lines in the above list item is the keyid but I am clueless.

Thoughts?

---

### Post by deadflowr on 2020-01-23
The keyid should be the last 8 digits: 9798C2FC in line two.
For reference: [https://askubuntu.com/a/846877]("https://askubuntu.com/a/846877")

---

### Post by jgw on 2020-01-27
Thank you! 

It worked!

---

