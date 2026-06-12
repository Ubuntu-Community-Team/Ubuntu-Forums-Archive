---
title: "Cannot find -lz | ld returned 1 exit status | command 'x86_64-linux-gnu-gcc' failed.."
date: 2016-03-11
forum: General Help
---

### Post by taiwo3 on 2016-03-11
Hello,

I have been trying to install GNU Health 3.0 on Ubuntu 15.10 but I am encountering the below errors. I have also tried several fixes but it keeps giving same errors. 

Any help please?


Result after running command line ./gnuhealth-setup install
```


x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security -Wl,-Bsymbolic-functions -Wl,-z,relro -D_FORTIFY_SOURCE=2 -g -fstack-protector-strong -Wformat -Werror=format-security build/temp.linux-x86_64-2.7/src/lxml/lxml.etree.o -lxslt -lexslt -lxml2 -lz -lm -o build/lib.linux-x86_64-2.7/lxml/etree.so


/usr/bin/ld: cannot find -lz


collect2: error: ld returned 1 exit status

error: command 'x86_64-linux-gnu-gcc' failed with exit status 1

----------------------------------------
Cleaning up...
Command /usr/bin/python -c "import setuptools, tokenize;__file__='/tmp/pip-build-SiSPXw/lxml/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-w8kYiH-record/install-record.txt --single-version-externally-managed --compile --user failed with error code 1 in /tmp/pip-build-SiSPXw/lxml
Storing debug log for failure in /home/gnuhealth/.pip/pip.log

[15:43:46][INFO] Bailing out !

[15:43:46][INFO] Cleaning up temp directories at /tmp/gnuhealth_installer

[15:43:46][INFO] removing base dir at /home/gnuhealth/gnuhealth
gnuhealth@taiwo-MacBookPro:~$ 




```

---

### Post by steeldriver on 2016-03-11
Hello and welcome to the forums

What fixes have you tried? It looks like you need to install the zlib development package, zlib1g-dev

---

### Post by taiwo3 on 2016-03-15
Hi steeldriver,

Thanks for your swift reply. I have installed 'zlib1g-dev' and it appeared to have cleared the errors, just to bring up another requesting me to install 'libpq-dev' which I did. The latest errors after the installation of libpq-dev are 'manifest_maker: standard file '-c' not found' and 'ValueError: --enable-jpeg requested but jpeg not found, aborting.'...researching on them now. 

Earlier, I had applied 'lxml2' fix which brought about the errors I posted initially.

---

