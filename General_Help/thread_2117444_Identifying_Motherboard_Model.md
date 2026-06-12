---
title: "Identifying Motherboard Model"
date: 2013-02-18
forum: General Help
---

### Post by Kodeine on 2013-02-18
Salutations!

So upon upgrading my motherboard and CPU when Haswell arrives I'd like to sell off my old processor and motherboard. The processor is much easier to identify but the motherboard is not. Some googling returned many different commands to find information about the motherboard but lots of entries where listed as 'to be filled in by OEM'. How can I find out what make and model it is?

---

### Post by ibjsb4 on 2013-02-18
```
sudo lshw
```

Should spit out a mile long list that hopefully will contain your MB :)

---

### Post by slickymaster on 2013-02-18
[Follow these clues to find a motherboard's manufacturer]("http://www.techrepublic.com/article/follow-these-clues-to-find-a-motherboards-manufacturer/1041092")

---

### Post by slickymaster on 2013-02-18
Don't know if you already tried it:
```
dmidecode --type baseboard
```

---

