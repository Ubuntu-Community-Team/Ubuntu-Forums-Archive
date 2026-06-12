---
title: "Dirvish, why is my back-up deleted after 3 months!?"
date: 2022-11-04
forum: General Help
---

### Post by civilpolisen on 2022-11-04
[PHP]#xdev: 0

expire-default: +15 days
expire-rule:
#   * * * * fri  +1 months
#   * * 1 * *    +24 months
# Settings from page 18+19 in users guide:
# https://sanctum.geek.nz/presentations/incremental-backups-dirvish.pdf

#       MIN HR    DOM MON       DOW  STRFTIME_FMT
#        *   *     *   *         1  +3 months
        *   *     1-7 *         1  +1 year
        *   *     1-7 1,4,7,10  1
#        *   10-20 *   *         *    +4 days
#        *   *     *   *         2-7  +15 days
[/PHP]

We use Dirvish default settings, as in this link: [https://dirvish.org/debian.howto.html](https://dirvish.org/debian.howto.html)
Or... to be more correct...  we used to have the default settings and  that's when we discovered this summer that backup from last November was not present!
We don't need anything fancy! Just the default settings!
Please guide me! What am I missing!?

---

