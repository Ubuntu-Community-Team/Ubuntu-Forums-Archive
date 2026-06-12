---
title: "Ansible Problem with Yaml file trying to deploy a docker container"
date: 2020-01-09
forum: General Help
---

### Post by jcrespin101 on 2020-01-09
Hey guys i have problems with Ansible YAML files, i validate my YAML file with a web and still dont working, is just a question if u know what is going on with my file . i Post all u need , im trying to deploy a docker container on my "client" .

MY FILE:

[IMG]https://gyazo.com/d93d9bfb0a82f51e622dfa00dce0c2f7[/IMG][https://gyazo.com/d93d9bfb0a82f51e622dfa00dce0c2f7](https://gyazo.com/d93d9bfb0a82f51e622dfa00dce0c2f7)

THE "ERROR"

[https://gyazo.com/782b176b3cd8bbb050af3a115168a97b](https://gyazo.com/782b176b3cd8bbb050af3a115168a97b)

-ANSIBLE VERSION:

 2.0.0.2

-DOCKER VERSION:

18.09.7

If u need more things pls tell me , i'm deeply confused with this thing .

---

### Post by kevdog on 2020-01-10
Your syntax looks wrong:

It should be
```
- name:
  docker-container: (etc)
```

---

