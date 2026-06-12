---
title: "Script to Create a Text File with My ifconfig Info"
date: 2013-09-18
forum: General Help
---

### Post by chiques on 2013-09-18
Hello Community,
I'm trying to figure out how to create a script which will write a text file of my ifconfig info. So far I have this but I don't know what will save it into the *.txt file.

```

#!/bin/bash
echo "My ifconfig info is:"
ifconfig

```

After I run the .sh file, I would create a ifconfig.txt file.

Thanks for any help.

---

### Post by papibe on 2013-09-18
Hi chiques.

Just redirect the output from the standard (terminal) to a file. For instance:
```
#!/bin/bash
echo "My ifconfig info is:" > interface.txt
ifconfig >> interface.txt
```
Alternatively, you could leave it like it is and redirect the output on the call itself:
```
./yourscript.sh > interface.txt
``` 
Hope it helps. Let us know how it goes.
Regards.

---

### Post by chiques on 2013-09-20
Hi papibe,
Yeah, that's pretty much what I ended up doing. I thought there was a way to do it all in one script but why make things more difficult that they have to be. Thanks!

---

