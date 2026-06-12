---
title: "Dlink DI-624s Source Code"
date: 2008-07-08
forum: General Help
---

### Post by danrulz98 on 2008-07-08
I have a Dlink DI-624s router that has NEVER worked properly. After over a year, I deiced to try and compile the source code and try to get a working firmware. 
In the README that came with the firmware package, it said to run 
```
make xconfig
``` 
I did that, and it went through the whole config process without errors. The next step in the README is to run 
```
make dep
```
I do that and all I get is this
```
daniel@danzlaptop:~/Desktop/dlink/DI-624s_v100036$ make dep
echo '#define PKG_VERSION "0.6.5-2"' > linux-2.4.x/drivers/net/re865x/version.h
/bin/sh: /opt/toolchain_mips/bin/mips-linux-gcc: not found
/bin/sh: /opt/toolchain_mips/bin/mips-linux-gcc: not found
/bin/sh: /opt/toolchain_mips/bin/mips-linux-gcc: not found
echo '#define ROMEDRIVER_VERSION "3.5-2"' >> linux-2.4.x/drivers/net/re865x/version.h
ln  -fs /home/daniel/Desktop/dlink/DI-624s_v100036/linux-2.4.x/drivers/net/re865x/version.h include/;\
	if [ ! -f include/re865x.h ] ; then \
		ln  -s /home/daniel/Desktop/dlink/DI-624s_v100036/linux-2.4.x/include/asm/rtl865x/re865x.h include/re865x.h;\
	fi
ln: creating symbolic link `include/re865x.h': File exists
make: *** [dep] Error 1
daniel@danzlaptop:~/Desktop/dlink/DI-624s_v100036$ 

```
What am I doing wrong? Any suggestions at all?

---

