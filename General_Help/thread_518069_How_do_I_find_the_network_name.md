---
title: "How do I find the network name?"
date: 2007-08-05
forum: General Help
---

### Post by woof65 on 2007-08-05
I'm trying to set up remote administration of an app I have running on 7.04. The instructions has a line that reads as follows:

"Replace references to 'localhost' in the BASServer.props file located in the BIN directory of the AwareIM installation on the server machine with the network name of the server machine, for example:
           DirectoryServiceProvider+jnp\://myserver\:1099/"

I need to find out what I need to change the "myserver" part to. On Windows and Mac OS X, I can find it pretty easily, but as a Linux noob, I can't seem to locate it. Could anyone please help?

---

### Post by dreadlord_chris on 2007-08-05
> **woof65 said:**
> I'm trying to set up remote administration of an app I have running on 7.04. The instructions has a line that reads as follows:

"Replace references to 'localhost' in the BASServer.props file located in the BIN directory of the AwareIM installation on the server machine with the network name of the server machine, for example:
           DirectoryServiceProvider+jnp\://myserver\:1099/"

I need to find out what I need to change the "myserver" part to. On Windows and Mac OS X, I can find it pretty easily, but as a Linux noob, I can't seem to locate it. Could anyone please help?

```

hostname

```

---

