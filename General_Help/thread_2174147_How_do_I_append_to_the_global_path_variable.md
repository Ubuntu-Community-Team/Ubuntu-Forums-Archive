---
title: "How do I append to the global path variable"
date: 2013-09-13
forum: General Help
---

### Post by narunaram on 2013-09-13
Hi,

I have Ubuntu 13.04. I want to append to the global path variable. Can you please guide.. I tried modifying the environment file at /etc/environment.. but that file seems to be readonly and it gives me permission denied error.

Thanks
Naresh

---

### Post by coffeecat on 2013-09-13
Not a Forum Feedback & Help thread.

*Thread moved to **General Help**.*

---

### Post by Crusty Old Fart on 2013-09-13
> **narunaram said:**
> Hi,

I have Ubuntu 13.04. I want to append to the global path variable. Can you please guide.. I tried modifying the environment file at /etc/environment.. but that file seems to be readonly and it gives me permission denied error.

Thanks
Naresh
There is more than one way to do what you're asking. My preference is to add a line to the bottom of the file: ~/.bashrc that looks similar to this:
```

export PATH=$PATH:/path/to/directory

```
After adding the line above, you can force the change to take effect immediately with the following command:
```

source ~/.bashrc

```
Then, you can check your PATH variable to make sure it was appended with the following command:
```

echo "PATH = $PATH"

```
If this doesn't work for you, you may want to examine your ~/.profile file for the cause.

---

