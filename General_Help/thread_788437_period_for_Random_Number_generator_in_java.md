---
title: "period for Random Number generator in java"
date: 2008-05-09
forum: General Help
---

### Post by dhartasa on 2008-05-09
I need to know what is the period of the random number generator in java (that comes with Ubunto)

---

### Post by andrewc6l on 2008-05-09
I believe that's the Apache Harmony java.util.Random. According to the javadoc for next():

Implements D. H. Lehmer's random number algorithm found in The Art of Computer Programming, Volume 2: Seminumerical Algorithms, by Donald E. Knuth (section 3.2.1).

If I remember correctly, the period is the multiplier - 1 if the multiplier is prime. That would make the period 25214903916, since the multiplier is 25214903917. (Assuming that's a prime - I haven't checked.) It may be longer than that since it adds a constant... it's been too long since I did this :-)

---

