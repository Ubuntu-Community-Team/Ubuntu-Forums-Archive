---
title: "SSH files &amp; folders with dates kept intact"
date: 2016-02-27
forum: General Help
---

### Post by Macamba on 2016-02-27
Is it possible to use SSH to transfer files and folders to another system while keeping the creation dates of these files and folders?

---

### Post by deadflowr on 2016-02-27
I think sshfs works to do that.
As it mounts the ssh'd directory of your choice locally in your client.
so it acts and behaves like any other folder in your client machine.

Or at least that is how it works for me.

You install it on the client side.

---

### Post by Macamba on 2016-02-27
Thanks.

---

### Post by SeijiSensei on 2016-02-27
If you use "rsync -a" it will connect over SSH and transfer the files while keeping permissions and dates intact.

---

### Post by The Cog on 2016-02-27
**scp -p** also preserves dates etc.

---

