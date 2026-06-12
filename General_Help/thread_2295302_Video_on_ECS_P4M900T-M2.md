---
title: "Video on ECS P4M900T-M2"
date: 2015-09-17
forum: General Help
---

### Post by tamir2 on 2015-09-17
Is it possible to get a normal vertical sync without delay on the ECS P4M900T-M2? Technical details - [http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=822&LanID=6&MenuID=16](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=822&LanID=6&MenuID=16)
OS - Xubuntu 14.04.2 kernel 3.16.

---

### Post by tamir2 on 2015-09-17
&#1057;an someone tell me what kind of graphics card installed on the motherboard ECS P4M900T-M2 that it would be better supported by ubuntu?

---

### Post by cariboo on 2015-09-17
Could you open a terminal and type:

```
sudo lshw -C display
```

and paste the output in your next post.

---

### Post by tamir2 on 2015-09-18
```

sudo lshw -C display

```
* -display UNCLAIMED
        Description: VGA compatible controller
        Product: CN896 / VN896 / P4M900 [Chrome 9 HC]
        Manufacturer: VIA Technologies, Inc.
        Physical ID: 0
        information about the bus: pci @ 0000: 01: 00.0
        Version: 01
        Resolution: 32 bits
        Frequency: 66MHz
        capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
        the configuration: latency=64 mingnt=2
        resources: memory:d8000000-dfffffff memory:fd000000-fdffffff memory:feaf0000-feafffff

---

