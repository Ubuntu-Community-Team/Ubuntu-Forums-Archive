---
title: "fallocate failed: Operation not supported"
date: 2014-12-25
forum: General Help
---

### Post by john338 on 2014-12-25
When running,

```
fallocate -l 10G /path/to/file
```  

I'm returned the following error:

  ```
fallocate: file: fallocate failed: Operation not supported
``` 

Creating the file using dd (if=/dev/urandom) works,  but if I'm trying to create large files, tens of GBs in size, it takes  several hours to complete.

  Running Ubuntu 14.04. Using an ext4 partition, specifying a file-type doesn't appear to alter the outcome.

  Working fine on my CentOS machines, just not Ubuntu.

---

