---
title: "Problem with vmware installation, help!!"
date: 2007-10-09
forum: General Help
---

### Post by definewebsites on 2007-10-09
I tried installing vmware server, and encountered problems. It was asking me for directories where things were located and I just kept pressing enter as I wasn't sure what to do, then the installation just ended with an error.

When I tried to run it again, it said that "previous installation of vmware detected", even though the installation never completed.

Now I cannot find anyway to remove what has been done.

Any ideas..

:(

---

### Post by tszanon on 2007-10-09
> **definewebsites said:**
> I tried installing vmware server, and encountered problems. It was asking me for directories where things were located and I just kept pressing enter as I wasn't sure what to do, then the installation just ended with an error.

When I tried to run it again, it said that "previous installation of vmware detected", even though the installation never completed.

Now I cannot find anyway to remove what has been done.

Any ideas..

:(
Are you installing from Feisty repositories or the tarball from [www.vmware.com?](www.vmware.com?) If it's from the site, then you probably have not installed the package build-essentials. If I recall correctly, it will install the linux headers and the gcc compiler (both are needed for installing vmware).

---

### Post by definewebsites on 2007-10-09
Hi, thanks for the response..

I have installed the package:  build-essentials , but I developed that problem anyway.

:(

---

### Post by tszanon on 2007-10-09
> **definewebsites said:**
> Hi, thanks for the response..

I have installed the package:  build-essentials , but I developed that problem anyway.

:(
A few questions:
1. What version of Ubuntu are you using (Dapper, Feisty,...)?
2. Are you installing vmware using synaptic or have you downloaded the file from the site [http://www.vmware.com](http://www.vmware.com) ?
3. What's the error message?

---

### Post by definewebsites on 2007-10-10
Hi there,

Thanks for the response:

1) I am using Ubuntu(Gutsy) version 7.10

2) I downloaded vmware from the website [www.vmware.com](www.vmware.com)

3) The error message is of this form:

"Previous installation of vmware detected, error, cannot proceed"

However that is ironic, as the installation never got underway as I described in the first post. It just asked me where I would like to install the program, then some directorys where files were located, I pressed enter on each one thinking that it would use what was there as default, then the installation just aborted. When I tried running it again afterwards, thats when I got the error message above.

Thanks

:(

---

### Post by zvacet on 2007-10-10
Go to the **etc** and delete vmware folder.

---

### Post by definewebsites on 2007-10-10
Thanks for the response..

I tried deleting the vmware folder from /etc , but for some reason it would not permit me to do so..

Any idea why?

Thanks

:(

---

### Post by tszanon on 2007-10-10
> **definewebsites said:**
> Thanks for the response..

I tried deleting the vmware folder from /etc , but for some reason it would not permit me to do so..

Any idea why?

Thanks

:(
It happened because you don't have the right to do so. In order to delete that folder, you must be root:
1. Press ALT + F2. A dialog box will appear;
2. Type:
```
gksudo nautilus
```
3. It will ask for your password;
4. Nautilus will be run as root. Now, go to /etc and delete the folder. **[COLOR="Red"]BEWARE:[/COLOR]** you will be able to do anything, including deleting important files and folders. Make sure that you close that Nautilus window as soon as you delete the vmware folder.

Now, try to install it again. Everything should be fine.

**Edit:** Isn't it available in Gutsy repositories too? Since you can install vmware-server in Feisty using synaptic, probably you can do it in Gutsy too.

---

### Post by definewebsites on 2007-10-14
Hi there,

I logged in as administrator by running the 'gksudo nautilus', but it still would not permit me to delete it. I have noticed that under the permissions, it is on read-only, and it would not permit me to alter the permissions.

I tried deleting it from the terminal, but with no luck. Any idea why it has been locked even when I am running as root on my system?

Thanks

:(

---

### Post by Tlon on 2007-10-14
I'm having problems getting vmware to work in Gutsy as well.  So far I've only tried installing via Synaptic (glad I checked before going further).  First I was alerted that I'd be installing a package that could not be authenticated, and then when I tried to proceed I was presented with the error:

vmware-player:
 Depends: vmware-player-kernel-modules  but it is not installable


D'oh.

---

### Post by zvacet on 2007-10-14
@definewebsites

Login with admin rights and go to the etc by cd /etc and 

```
sudo rm -r folder_name
``` 
 
Be sure that you type exact name of folder.Good luck!

---

### Post by definewebsites on 2007-10-14
Hi, thanks for the response.

I have already tried using that command, when logged in as administrator, but the system says that I do not have the permissions to delete that folder.

I then tried to use the synaptic package manager to install vmware player as the fellow above, but I got the same error message that he did.

Any ideas

Thanks

:(

---

