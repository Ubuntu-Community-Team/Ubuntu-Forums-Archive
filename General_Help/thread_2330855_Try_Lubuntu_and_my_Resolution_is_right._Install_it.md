---
title: "Try Lubuntu and my Resolution is right. Install it and I can't change resolution."
date: 2016-07-15
forum: General Help
---

### Post by igorzovisk on 2016-07-15
There's no resolution but 640x480.

When I do sudo lshw -C video
This appear:
*-display DISPONÍVEL            descrição: VGA compatiblecontroller
produto: 82G33/G31 Express Integrated Graphics Controller
fabricante: Intel Corporation
ID físico: 2
informações do barramento: pci@0000:00:02.0
versão: 10
largura: 32 bits        clock: 33MHz
capacidades: msi pm vga_controller bus_master cap_list
configuração: latency=0
recursos:
memória:fe980000-fe9fffff
porta de E/S:cc00(tamanho=8)
memória:d0000000-dfffffff
memória:fe800000-fe8fffff

What that could be?

---

### Post by igorzovisk on 2016-07-15
Did this: [https://ubuntuforums.org/showthread.php?t=2260082](https://ubuntuforums.org/showthread.php?t=2260082)
Worked.

---

