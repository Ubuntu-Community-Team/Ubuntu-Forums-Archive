---
title: "Help with &quot;convert -crop&quot; for image cropping - using the terminal"
date: 2023-01-02
forum: General Help
---

### Post by DVD-R on 2023-01-02
Hello All,
I need some help understanding how the parameters work with the convert -crop command for cropping an image.

Lets say - I use the "identify" command to get the image info

result:
1366x768 1366x768+0+0 8-bit sRGB 189666B 0.000u 0:00.000

Ok the image size is 1366x768

Now lets say I want to crop the following:

From the left - remove 10 pixels
From the right - remove 15 pixels
From the top - remove 20 pixels
From the bottom - remove 25 pixels

What would the correct convert -crop syntax be for that process?

Sincere thanks!

---

### Post by Holger_Gehrke on 2023-01-02
The -crop option takes a geometry argument of the form widthxheight+horizontalOffset+verticalOffset. So for your example I get '-crop 1341x723+10+20' (1366-10-15=1341;768-20-25=723).

Holger

---

### Post by DVD-R on 2023-01-02
Thank you Holger_Gehrke!
I will try that!

Very sincere thanks!

---

