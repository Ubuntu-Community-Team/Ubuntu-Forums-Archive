---
title: "UFW blocks NFS"
date: 2019-06-11
forum: General Help
---

### Post by Neill_R on 2019-06-11
Hello

I have an NFS server running on my server (10.10.1.40). On a client I have the NFC client set up. On the server 

```


**showmount -e localhost**

Export list for localhost:
/srv/nfsshare   10.10.1.0/24
/mnt/Music      10.10.1.0/24
/mnt/wikidata   10.10.1.0/24
/mnt/publicdata 10.10.1.0/24

neill@Xeon-host:~$ **showmount -e 10.10.1.40**
Export list for 10.10.1.40:
/srv/nfsshare   10.10.1.0/24
/mnt/Music      10.10.1.0/24
/mnt/wikidata   10.10.1.0/24
/mnt/publicdata 10.10.1.0/24
neill@Xeon-host:~$ 


```

On the client with the server firewall on

```


[B]showmount -e 10.10.1.40
[/B]
rpc mount export: RPC: Timed out


```

with the server firewall Off

```


[B]showmount -e 10.10.1.40
[/B]
Export list for 10.10.1.40:
/srv/nfsshare   10.10.1.0/24
/mnt/Music      10.10.1.0/24
/mnt/wikidata   10.10.1.0/24
/mnt/publicdata 10.10.1.0/24
neill@SSD-Mint-64:~$ 


```

My questions is what commands do i run to see what is being blocked when the firewall is on

Thank you

---

### Post by SeijiSensei on 2019-06-11
Is there a reason you don't have a general ACCEPT rule for all machines on the 10.10.1.0/24 network?

---

