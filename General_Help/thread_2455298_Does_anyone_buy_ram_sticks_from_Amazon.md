---
title: "Does anyone buy ram sticks from Amazon?"
date: 2020-12-17
forum: General Help
---

### Post by sofasurfer on 2020-12-17
I need to add some ram to my pc. I'd like to get 4 gig (ddr3 1333) As I am in an extreme money crunch right now I am looking at Amazon for a good deal. Best buy is quite expensive in comparison. Amazon has 4 gig for about $9.50. ( [https://www.amazon.com/s?k=ddr3+ram&i=computers&rh=n%3A172500%2Cp_n_feature_four_browse-bin%3A2253866011%2Cp_n_feature_five_browse-bin%3A673263011&s=price-asc-rank&dc&qid=1608183476&rnid=673240011&ref=sr_st_price-asc-rank](https://www.amazon.com/s?k=ddr3+ram&i=computers&rh=n%3A172500%2Cp_n_feature_four_browse-bin%3A2253866011%2Cp_n_feature_five_browse-bin%3A673263011&s=price-asc-rank&dc&qid=1608183476&rnid=673240011&ref=sr_st_price-asc-rank) )   
I am not sure if cheap brands are a disappointment waiting to happen. Supermicro, Fujitsu etc. Also, is DDR3 the only spec I need to know about?

---

### Post by crip720 on 2020-12-17
DDR3 is just the basic family name of ram you need.  Also need to match type of dimm and pins and speed.  Would google your computer make and model with ram to find all the specs.  Can use faster speed, but the speed will be dropped to match the ram you have now.  Amazon/ebay will usually have lower prices than box stores.

---

### Post by CelticWarrior on 2020-12-17
... and Aliexpress even cheaper, generally.

Some specialized online stores like Crucial and MemoryC have a searchable online database to match supported RAM modules to your computer. You can use those to find out the maximum capacity supported and recommended frequency. Then search other stores for a better price.

---

### Post by ActionParsnip on 2020-12-17
Does the system have a make and model? If you are unsure then you can run
```

sudo dmidecode -t 1

```
and give us the output

---

### Post by sofasurfer on 2020-12-19
I neer noticed before, but my terminal prompt actually have the make and model of my motherboard. I is a Dell Inspiron 660. I currently have only 2 gigs of ram in 1 of the 2 dimm slots. So if I get 4 gigs in 1 slot I can add another later. I don't think I can add a 4 gig stick alongside of the current 2 gig stick. So I guess what I am asking is, what exact memory do I need and where is the least expensive place to buy it that sell dependable memory sticks? BTW, I looked in the manual for the MB and it does not even say what memory I should use. Isn't that odd? I also will need a new hard drive and I only need about 250 gigs or so. No terrabytes needed. I read that SSD is cheaper than HDD but it is that opposite at Best Buy. So I guess I need HDD.

 ```
 Memory Device
	Array Handle: 0x0010
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: 00
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Micron
	Serial Number: DC74B268
	Asset Tag: 9876543210
	Part Number: 8JTF25664AZ-1G4D1 
	Rank: 1
	Configured Clock Speed: 1333 MHz
 
```

---

### Post by SeijiSensei on 2020-12-20
Newegg has a memory finder. Here's what I get for the Inspiron 660:

[https://www.newegg.com/tools/memory-finder?Category=AA&name=Dell+Inspiron+660&Manufactory=351961&ProductLine=155127+670092&Model=1227077&Order=1](https://www.newegg.com/tools/memory-finder?Category=AA&name=Dell+Inspiron+660&Manufactory=351961&ProductLine=155127+670092&Model=1227077&Order=1)

4GB modules start at around $16.

---

### Post by mIk3_08 on 2020-12-20
I think any brand is good as long as it will work and it suits the specification of your machine it will be more better. I am also planning to add up a ram of my machine but I don't have any budget yet. If you need more options just [Click here]("https://www.google.com/search?biw=1745&bih=778&ei=qYXfX9bwG6a1tgXO65-IAw&q=ddr3+memory+4gb+for+sale&oq=ddr3+memory+4gb+for+sale&gs_lcp=CgZwc3ktYWIQAzIJCAAQyQMQFhAeMgYIABAWEB4yBggAEBYQHjoECAAQR1DbgQRYqYkEYJGRBGgAcAJ4AIABlgaIAYUJkgEHMy0xLjYtMZgBAKABAaoBB2d3cy13aXrIAQjAAQE&sclient=psy-ab&ved=0ahUKEwiW6ZPqht3tAhWmmq0KHc71BzEQ4dUDCA0&uact=5")

---

### Post by Frogs Hair on 2020-12-20
Just ordered 2x4 GB from Amazon and it is about the same price as Ebay for new stock. Knowing what speed and the pin count is very important . Memory finder tools as linked above are very helpful for this.

---

