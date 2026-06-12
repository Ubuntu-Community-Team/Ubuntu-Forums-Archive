---
title: "php path"
date: 2007-02-17
forum: General Help
---

### Post by tamray on 2007-02-17
I have php5 installed on 6.10. What is the actual path to php in this case? I have a script I need to change the usual /usr/bin/php path on, but don't know what to enter.

Raymond

---

### Post by nereid on 2007-02-17
A simple 

```

which php

```

should reveal the path to your php binary.

---

### Post by tamray on 2007-02-17
I tried that earlier. It doesn't give me any info.

---

### Post by nereid on 2007-02-18
Maybe you should try it again with sudo

```

sudo which php

```

If this doesn't find anything, then maybe you only have mod_php, the Apache plugin, installed and not the php script binary.

---

### Post by Bad.Andy on 2007-02-22
I'm running in to the exact same issue. I even tried switching to php4 but still no dice..

Does anybody know what I can to find or install the php binary?

Thanks,
Andy

running: Kubuntu 6.10 w/ php5

---

### Post by Bad.Andy on 2007-02-22
Sorry to spam up the forums folks, I figured it out now...

I was missing the php5-cli package. Now its in /usr/bin/php

---

### Post by tlsarles on 2007-03-08
OMG Thank you. I was having the same issue. Seems odd that this isn't included in the default LAMP install

---

### Post by nereid on 2007-03-08
Why should it? Why do you need the command line interpreter for PHP?

---

### Post by rocktorrentz on 2007-03-15
Same problem trying to use this script; [http://www.pge.cl/~wawi/?page=phpdyndns](http://www.pge.cl/~wawi/?page=phpdyndns)

Thanks

---

### Post by Bad.Andy on 2007-03-15
Did you try installing php5-cli? That did it for me.

sudo apt-get install php5-cli

---

