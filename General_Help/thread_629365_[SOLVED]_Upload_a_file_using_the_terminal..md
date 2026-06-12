---
title: "[SOLVED] Upload a file using the terminal."
date: 2007-12-02
forum: General Help
---

### Post by TidusBlade on 2007-12-02
I run a server using SSH, anyways since I am using the terminal to connect to it, can somebody tell me a way to upload a file anywhere using only the terminal, and/or a service that would let me do that :D 
Thanks!

---

### Post by LSMadsen on 2007-12-02
You can use scp to do this, which you can read more about in "man scp"

But the standard syntax to upload is:
```
scp path_to_file/file username@server:path_to_upload_to
```

And to download is:
```
scp username@server:path_on_server/file path_to_download_to
```

---

### Post by TidusBlade on 2007-12-02
Thanks for that :D

---

