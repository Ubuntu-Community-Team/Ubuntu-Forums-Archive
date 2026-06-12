---
title: "Ubuntu Core and microK8s Cluster having a failing Coredns"
date: 2023-08-05
forum: General Help
---

### Post by allards on 2023-08-05
System works fine, but won't run Longhorn:

```


error
longhorn-system  longhorn-csi-plugin-dlwgh                &#9679;  2/3          0 CreateContainerError 
longhorn-system  longhorn-manager-759lc                   &#9679;  0/1          0 CreateContainerError
 


/etc/host
127.0.1.1 mcrks01 mcrks01
127.0.0.1 localhost


192.168.1.225 mcrks01
192.168.1.226 mcrks02
192.168.1.227 mcrks03
192.168.1.228 mcrks04
192.168.1.229 mcrks05
192.168.1.230 mcrks06


```



After a long troubleshooting session with ChatGPT it seems that CoreDNS is the problem.

sudo microk8s kubectl logs coredns-6f5f9b5d74-gf7g4 -n kube-system
Error from server: Get "https://192.168.1.225:10250/containerLogs/kube-system/coredns-6f5f9b5d74-gf7g4/coredns": tls: failed to verify certificate: x509: cannot validate certificate for 192.168.1.225 because it doesn't contain any IP SANs

Tried so far:
- date and time same on all system
- can nc between nodes into 10250
- did a MicroK8s  leave and reset

No idea how to fix this!?

Perhaps I should go back to normal Ubuntu!?

---

