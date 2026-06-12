---
title: "Photo Management with Facial Recognition"
date: 2018-02-12
forum: General Help
---

### Post by DarkHelmut on 2018-02-12
Hi, I have a simple Ubuntu server setup as my home server and amongst other things I've stored all my photos on it.  I'm wondering if someone can point me in a direction of any photo management software that does facial recognition that I can use to group my photos (about 15,000) and make those groupings available to other computers (windows, mac) on the home network.  

I've started to research this but not yet found many options.  And what I've found so far doesn't seem to offer the ability for other computers to benefit from the results (e.g. fotobounce, but maybe I'm wrong).

Just looking for any pointers that anyone can provide.

Thanks in advance.

Robnw

---

### Post by Ralph L on 2018-02-15
Digikam has an experimental face recognition feature.  I have never tried it.  

Ralph

---

### Post by DarkHelmut on 2018-02-15
Thanks Ralph.  Do you know if Digikam "output" can be accessed from other computers on the network?

---

### Post by dragonfly41 on 2018-02-16
For serious face recognition experiments you could try some of the cloud based services.
IBM Watson is on the short list.
[https://steemit.com/machinelearning/@cristi/machine-learning-for-facial-detection-and-face-recognition-watson-tutorial](https://steemit.com/machinelearning/@cristi/machine-learning-for-facial-detection-and-face-recognition-watson-tutorial)

---

### Post by DarkHelmut on 2018-02-16
Thanks dragonfly41.  Is there a way to use Watson to classify pictures (current set and future additions) so other users on other computers on the network can see the classifications?

---

### Post by dragonfly41 on 2018-02-17
You will gain a lot of detailed information by browsing the IBM blogs.

Here is just one.

[https://www.ibm.com/blogs/bluemix/2016/02/openwhisk-and-watson-image-tagging-app/](https://www.ibm.com/blogs/bluemix/2016/02/openwhisk-and-watson-image-tagging-app/)

**Q.**

[COLOR=#323232]This is exciting and will like to know if the system can be trained to recognize sometimes not so famous personalities.. Essentially, can I load my client images for recognition (private data of course..)[/COLOR]

**A.**

[COLOR=#323232]You can&#8217;t add your own images/faces to AlchemyAPI Face Detection feature. However you can use the Watson Visual Recognition service to build your own image classifiers tailored to your needs. Here is the link to the details [/COLOR][http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/doc/visual-recognition/customizing.shtml](http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/doc/visual-recognition/customizing.shtml)


Note this is an old blog and the redirected site is here ..
[https://console.bluemix.net/docs/services/visual-recognition/customizing.html#guidelines-for-training-classifiers](https://console.bluemix.net/docs/services/visual-recognition/customizing.html#guidelines-for-training-classifiers)


Read through .. and in particular .. training custom classifiers.

...

Looking at my IBM Cloud catalog page this is the summary of pricing ... for a free Lite Plan.

> 
Lite
7500 Events (images) towards General and Face Models
1 Custom Model
5000 Events (images) towards Custom Model
1 Lite Plan Instance per Bluemix Organization
Free
The Lite Plan allows users to make 7,500 API calls for free (up to 250 calls per day) and train a Custom Model using up to 5,000 images. Lite Plan services are deleted after 30 days. Users wishing to continue using the service must upgrade to a Standard Plan and receive a new API key.

Lite plan services are deleted after 30 days of inactivity.


---

