---
title: "Automatic fan control?"
date: 2014-08-03
forum: General Help
---

### Post by Ankush_Menat on 2014-08-03
Hellow I am running Ubuntu 14.04 but my laptop overheats a lot. CPU temp in "hardware sensor indicator" is ~55-60 degrees but I can feel lots of heat in some areas of laptop[(Lenovo G580]("http://www.flipkart.com/lenovo-essential-g580-59-358263-laptop-3rd-gen-ci5-4gb-500gb-dos/p/itmdcjhugdtpfzrk?pid=COMDGSR6RUYFGEGH&otracker=from-search&srno=t_4&query=lenovo+g580&ref=d08e0c50-cbbc-4f89-ae94-034f29c071e4")). However auto fan control never works, it always run at constant speed(which is slow afaik). Is there is any way I can make it run at full  speed for small periods so removes all hot air. Temp reaches to 60 even while light browsing (3-4 tabs at max)

---

### Post by Ankush_Menat on 2014-08-04
bump!?

Its overheting too much in but lm-sensors still says 53-60 degree...and fan still runs on constant slow speed.

---

### Post by Impavidus on 2014-08-04
We usually don't let the software interfere with the fans, although it can be done (don't ask me how). On my laptop, the fan switches to medium speed near 58ºC and full speed near 65ºC. Sometimes it reaches 80ºC. Intel says it's OK, the i5 CPU should trottle itself near 95ºC IIRC. So what's 55ºC?

But if it bothers you, you could check the ventilation of the box. Maybe there's dust in it, preventing the air from reaching all parts of the box, making some parts hot to touch. You can also check the actual load on your CPU. Run system monitor or the terminal program **top**, which will show you your actual CPU usage. Firefox with four tabs can mean anything, depending on the plugins you've running. If several pages use flash for example, usage goes up a lot.

---

### Post by Garchomps on 2014-08-04
[http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)

---

### Post by Ankush_Menat on 2014-10-16
> **Garchomps said:**
> [http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)
I enabled p-state as mentioned in tutorial, tried both TLP and Thermald but I am still getting 50C even when I've just finished bootup. After using it for 10 minutes it goes above 60 and it feels like sufficient to get burns.

---

