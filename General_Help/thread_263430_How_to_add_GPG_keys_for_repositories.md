---
title: "How to add GPG keys for repositories"
date: 2006-09-23
forum: General Help
---

### Post by leo_m on 2006-09-23
I tried to add these repositorie to get xgl/compiz,
> 
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
[http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
but I get these errors:

```

Reading package lists... Done
W: GPG error: [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems

```It asks me to run apt-get update to correct the problem, but the problem is reported by apt-get update itself!!

---

### Post by daller on 2006-09-23
You posted the answers yourself:

See these links:

[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)

[http://xgl.compiz.info/](http://xgl.compiz.info/)

---

### Post by leo_m on 2006-09-23
```

wget http://xgl.compiz.info/quinn.key.asc -O - | sudo apt-key add -

```worked though [http://xgl.compiz.info/](http://xgl.compiz.info/) resulted in 403

Thanks.

[Stands resolved]

---

