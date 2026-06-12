---
title: "GPU switching"
date: 2022-04-29
forum: General Help
---

### Post by zedular on 2022-04-29
Hello

I have Asus Strix 17 (G733QS), AMD Ryzen 9 5900 with RTX3080 GPU, how is it going with GPU switching between amd radeon (integrated on CPU) and Nvidia (discrete GPU). Is it posible like on Intel/Nvidia combo?

---

### Post by him610 on 2022-04-30
Although,I do not have your graphics chip combo. I only have discrete nvidia GFX on my systems
> Is it posible like on Intel/Nvidia combo?
I would think so. Probably will not hurt anything to try it. 
To select nvidia....
```

sudo prime-select nvidia

```
To select AMD... (I am guessing here)
```

sudo prime-select radeon

```

---

