---
title: "Beagle not updating search after file changes"
date: 2006-11-06
forum: General Help
---

### Post by Balachmar on 2006-11-06
I have two systems running Ubuntu, one is edgy and the other is dapper. I have installed beagle on both machines using Automatix.
On one machine (dapper) the search is automatically updated if I create a new file, or edit a file which meets the criteria
On the other machine (edgy) it doesn't. On the edgy machine I already have activated user_xattr
But that doesn't help. Also on the dapper machine user_xattr isn't even enabled in the mtab or fstab
The edgy is running the 2.6.17-10-generic kernel and the dapper machine is running the 2.6.15-27-386 kernel
So what can I do to fix this? Because I want the search to be automatically updated!

[edit]
Fixed it, by removing it through the package manager using complete removal.
Then reinstalling it using synaptic.
Now it works fine!

---

