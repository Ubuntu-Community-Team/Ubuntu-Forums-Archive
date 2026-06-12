---
title: "Ubuntu 14.04 LTS Running Slow on VirtualBox"
date: 2014-09-07
forum: General Help
---

### Post by AdHoc92 on 2014-09-07
Obviously, I don't expect it to be as snappy as a real installation, but it's quite choppy. I raised the memory from 1GB to 3GB with no improvement (I have 8 GB in total). Any solutions?

---

### Post by EuclideanCoffee on 2014-09-07
Are you running programs in the background? Did you check how much CPU other programs are taking?

It could be anything.

---

### Post by AdHoc92 on 2014-09-07
Memory usage is at 3GB and CPU usage is at most 17%. Cinnamon is telling me I'm "currently running without video hardware acceleration and, as a result, may observe higher than normal CPU usage"

---

### Post by EuclideanCoffee on 2014-09-07
> **AdHoc92 said:**
> Memory usage is at 3GB and CPU usage is at most 17%. Cinnamon is telling me I'm "currently running without video hardware acceleration and, as a result, may observe higher than normal CPU usage"

I'm speaking about your host system. The CPU is only 17%?

A few things that could sap your speed:
Resolution size
"Fall-back experience" video drivers

I ran Cinnamon in three cases. Each computer had a hard time keeping up with it, and that's why I don't use Cinnamon. Perhaps it's simply due to Cinnamon being an incomplete project at the moment. MATE might be a better option.

---

### Post by AdHoc92 on 2014-09-07
That is from my host system. I enabled 3 cores (out of 6) instead of 1 and it's working quite a bit better now. Firefox is still pretty slow though.

---

