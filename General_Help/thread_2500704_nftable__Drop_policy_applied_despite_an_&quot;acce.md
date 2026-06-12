---
title: "nftable : Drop policy applied despite an &quot;accept&quot; rule"
date: 2024-09-09
forum: General Help
---

### Post by nicoeverquest on 2024-09-09
Hello,


I add this rule to allow established connection :


nft add rule inet filter input ct state established,related accept


When the input policy is "accept" I can go on the internet.


But as soon as I set up the policy to "drop" I can't.


sudo nft add chain inet filter input '{ policy drop; }'


The policy normally applies when no rules are matched, so I don't understand why.


Here is my ruleset :




nicolas@localhost:~/Desktop$ sudo nft list ruleset


```
table inet filter {
chain input {
type filter hook input priority filter; policy drop;
ct state established,related accept
}


chain forward {
type filter hook forward priority filter; policy accept;
}


chain output {
type filter hook output priority filter; policy accept;
}
}

```
Thanks

---

### Post by Tadaen_Sylvermane on 2024-09-09
I am hardly an expert on nftables, or iptables as well but if it reads from top to bottom the 2 bottom rules never get to be applied. they are dropped immediately by the first rule.try putting drop on the bottom instead of the top? This assumes it works thte same as iptables does.

---

