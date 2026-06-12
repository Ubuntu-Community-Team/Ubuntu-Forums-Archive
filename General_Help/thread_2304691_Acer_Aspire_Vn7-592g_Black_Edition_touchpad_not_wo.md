---
title: "Acer Aspire Vn7-592g Black Edition touchpad not working with 4.2 kernel"
date: 2015-11-29
forum: General Help
---

### Post by db-d on 2015-11-29
Hi

I have a new Acer Aspire VN7-592g Black Edition with the following configuration:

[LIST]
[*]Item number: 5606957
[*]Screen size: 17.30 "
[*]Processor type: Intel Core i7-6700HQ
[*]Graphics card model: nVidia GeForce GTX 960M
[*]Memory: 32 GB
[*]Capacity SSD: 256 GB
[/LIST]

I use Ubuntu 14.04 and expect wireless and the touchpad it works quite good.
I use the upstream kernel 4.2.

The thing with the touchpad is quite strange. WIth the original 3.13. kernel the touchpad works. With the 4.2 kernel the touchpad is not even found.

When i show at the xinput info i looks like this:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=12    [slave  keyboard (3)]

```


Has anyone experience with this laptop and ubuntu or does someone know how i get this touchpad to run?

---

### Post by simone22 on 2015-11-29
I have the same laptop and I had the same problem, you just need to go to the bios settings and change the option on the touchpad, you need to put in something like always on... Not delay.

---

