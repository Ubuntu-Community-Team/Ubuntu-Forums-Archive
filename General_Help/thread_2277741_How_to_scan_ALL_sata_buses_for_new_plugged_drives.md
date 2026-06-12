---
title: "How to scan ALL sata buses for new plugged drives"
date: 2015-05-11
forum: General Help
---

### Post by robertco on 2015-05-11
Hello friends

this theoretically should work

```
for i in $(ls /sys/class/scsi_host/); do echo "- - -" > /sys/class/scsi_host/$i ; done
```

and instead i get this output

```

bash: /sys/class/scsi_host/host0: It's a directory
bash: /sys/class/scsi_host/host1: It's a directory
bash: /sys/class/scsi_host/host2: It's a directory
bash: /sys/class/scsi_host/host3: It's a directory
```

please note that the test I've done is this

```
for i in $(ls /sys/class/scsi_host/); do echo $i/scan; done
```

which output is

```

host0/scan
host1/scan
host2/scan
host3/scan
```

and since

```
echo "- - -" >/sys/class/scsi_host/host0/scan
```

is correct and works fine .. I'm wondering what is wrong with the cycle above

The cycle is needed to avoid repeating the command 4 times
```

# echo "- - -" >/sys/class/scsi_host/host0/scan
# echo "- - -" >/sys/class/scsi_host/host1/scan
# echo "- - -" >/sys/class/scsi_host/host2/scan
# echo "- - -" >/sys/class/scsi_host/host3/scan
```

Thank you for any hint

---

### Post by robertco on 2015-05-20
No one?

---

