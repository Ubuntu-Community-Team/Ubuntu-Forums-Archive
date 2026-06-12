---
title: "Installation of spd-say to /usr/local/bin throws error, why?"
date: 2020-05-03
forum: General Help
---

### Post by guest271314 on 2020-05-03
Installed **speech-dispatcher** from tarball [https://github.com/brailcom/speechd/releases/tag/0.10.0-rc3](https://github.com/brailcom/speechd/releases/tag/0.10.0-rc3). 

After running ```
$ ./configure && sudo make && sudo make install && sudo ldconfig
``` an error is thrown when running **spd-say**

```
speech-dispatcher-0.10.0-rc3$ sudo spd-say 'test'spd-say: symbol lookup error: spd-say: undefined symbol: spd_set_voice_pitch_range
```

See [https://github.com/brailcom/speechd/issues/301#issuecomment-623195421](https://github.com/brailcom/speechd/issues/301#issuecomment-623195421).

Ubuntu 18.04, 4.15.0-20-lowlatency, 32-bit.

How to fix?

---

### Post by guest271314 on 2020-05-03
Solved.

---

