---
title: "what to make of output from sensors command?"
date: 2008-03-07
forum: General Help
---

### Post by sloggerkhan on 2008-03-07
So I put together a new computer thursday... 

It seems to run fine, however, I find the output of the sensors command a little alarming.
Something is either wrong or misconfigured:
```

$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +10°C
Core0 Temp:
              +6°C
Core1 Temp:
              -3°C
Core1 Temp:
              +0°C

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:     +12.67 V  (min =  +0.00 V, max = +16.32 V)   
-12V:     -15.33 V  (min = -27.36 V, max =  +3.93 V)   
-5V:       +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
VBat:      +3.12 V
fan1:     4655 RPM  (min =    0 RPM, div = 2)          
fan2:     2860 RPM  (min =    0 RPM, div = 2)          
fan3:        0 RPM  (min =    0 RPM, div = 2)          
M/B Temp:    +27°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +30°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled   


```

What are the Core0 and Core1 readings actually looking at?
Temp3 I am assuming is somehow irrelevant as it says sensor = disabled.
But what's with all the voltage alarms?

Have I configured something wrong?
Do I need to change anything?
What is up with this?

---

### Post by PurposeOfReason on 2008-03-07
So you know what you choose for your sensors (i2c etc.)? A CPU that cold would be amazing, if it would even work.

---

### Post by sloggerkhan on 2008-03-07
I'm pretty sure that the temps given in the second part, under:
```

it8712-isa-0290
Adapter: ISA adapter

```
as 
```

it8712-isa-0290
Adapter: ISA adapter

```
are my actual CPU/mobo temps, as they match fairly closely the readings I can see in my BIOS.

I sorta doubt whatever is getting read as 0, 6, -3, and 10 are actual temps. My case doesn't have any frozen spots, lol, not to mention air cooled.
I also thing it would be odd for a dual core CPU to have 4 temp sensors.
I think the ISA numbers might be the more important ones. Don't really know. 

The modules I think are :
max6650
it87
k8temp

So in theory, the 
```

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
              +9°C
Core0 Temp:
              +5°C
Core1 Temp:
              -3°C
Core1 Temp:
              +3°C

```
is either some sort of CPU or mobo sensor.

---

### Post by PurposeOfReason on 2008-03-07
I also forgot to ask for the specs of it all. As detailed as possible (motherboard in particular).

---

### Post by sloggerkhan on 2008-03-07
[https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=7184811&WishListTitle=My+new+Ubuntu+PC](https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=7184811&WishListTitle=My+new+Ubuntu+PC)
Is the build.

45Watt AMD x2, 2.1 ghz, 2 gigs 1066 (533) RAM, 250 gb SATA HD, basic Asus micro ATX motherboard, mushkin 550 watt PSU, and a fanless 8600gt.

Mobo link here: [http://www.newegg.com/product/product.aspx?item=N82E16813131249](http://www.newegg.com/product/product.aspx?item=N82E16813131249)

---

### Post by dcstar on 2008-03-08
> **sloggerkhan said:**
> [https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=7184811&WishListTitle=My+new+Ubuntu+PC](https://secure.newegg.com/NewVersion/Wishlist/PublicWishDetail.asp?WishListNumber=7184811&WishListTitle=My+new+Ubuntu+PC)
Is the build.

45Watt AMD x2, 2.1 ghz, 2 gigs 1066 (533) RAM, 250 gb SATA HD, basic Asus micro ATX motherboard, mushkin 550 watt PSU, and a fanless 8600gt.

Mobo link here: [http://www.newegg.com/product/product.aspx?item=N82E16813131249](http://www.newegg.com/product/product.aspx?item=N82E16813131249)

"Brisbane" core AMD X2s have a know CPU diode temp reporting error - I add 20C to mine to get realistic readings.

---

### Post by sloggerkhan on 2008-03-08
does that mean my cpu temp is 50 C, or that for the sensors labeled core0 and core1 only I should add 20 C? 
edit: Looking it up, it looks like 30C is probably the motherboard CPU sensor, while the Core0/Core1 are probably the broken CPU internal probes. 
If this is the case, I wonder if there's a way to set the Core1/Core0 readings to display CPU Temp + Core0 (or core 1 and so on) so that they are probably more of a conservative overestimate of temp? 
Looking at other forums, I guess for now I'll just be ignoring those readings.

No comments about what the diabled temp3 might be?

And lastly, does anyone know anything about the voltage readings??
They are the thing that I'm really more worried about.

---

### Post by dcstar on 2008-03-08
> **sloggerkhan said:**
> 
............
No comments about what the diabled temp3 might be?

And lastly, does anyone know anything about the voltage readings??
They are the thing that I'm really more worried about.

The built-in formulas for a chipset are only a guess, and motherboard manufacturers are free to do all sorts of things that make the sensors defaults misleading.

You can go into your BIOS, make a careful note of all reported temps, fan speeds & voltages (their names and values), and then edit your /etc/sensors.conf file so the chipset used in there reports what is actually happening in your particular hardware.

With a little bit of experimentation you can get accurate output - but it may take some time (and then save the sensors.conf so it doesn't get overwritten by any future upgrades/installs).

---

### Post by sloggerkhan on 2008-03-08
damn, that sensors.conf file is intimidating....

---

