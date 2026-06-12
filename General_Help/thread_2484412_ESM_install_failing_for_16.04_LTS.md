---
title: "ESM install failing for 16.04 LTS"
date: 2023-02-25
forum: General Help
---

### Post by fahrbach on 2023-02-25
Hi, I'm getting this error when trying to install the extended security maintenance packages for 16.04 LTS:  E: Failed to fetch [https://plus-pkgs.nginx.com/ubuntu/dists/xenial/nginx-plus/binary-amd64/Packages](https://plus-pkgs.nginx.com/ubuntu/dists/xenial/nginx-plus/binary-amd64/Packages)  400  Bad RequestE: Some index files failed to download. They have been ignored, or old ones used instead.  

I keep getting 400 bad requests.  I there another site I can use?

I would like to enable esm apps and infra but I get when doing a status check:

SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-apps         yes       disabled  Expanded Security Maintenance for Applications
esm-infra        yes       disabled  Expanded Security Maintenance for Infrastructure
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service
ros              yes       disabled  Security Updates for the Robot Operating System
ros-updates      yes       disabled  All Updates for the Robot Operating System




I successfully installed ESM on another 16.04 LTS based machine; both machines have my Ubuntu token associated.  Any help is greatly appreciated and if this is the wrong forum please redirect.

Thanks,

Fred

---

### Post by fahrbach on 2023-02-25
Could this be that the server is not getting my SSL cert?  If that is the case how can I rectify?

---

### Post by ian-weisser on 2023-02-25
If you are paying customer for Pro/Advantage/esm (not the free  subscription tier), then contact your Canonical support representative (whom we are not).

Nobody, to my knowledge, provides free esm support -- that's why enterprises pay for it.

You are asking for support for a release of Ubuntu that we stopped supporting --including answering questions and assisting troubleshooting-- nearly two years ago.

The Ubuntu community has never provided esm support, and recommends  instead that you migrate to a newer, supported release of Ubuntu.

---

### Post by fahrbach on 2023-02-25
Thanks, Ian, it's my understanding that the Pro version for individuals with ESM installed will get security updates like patches for CVEs through 2026.  As I said, I have it running on another machine.  There is a reason why this ESM solution was offered. :-)

---

### Post by MAFoElffen on 2023-02-25
When I was testing Ubuntu Pro for the "Ubuntu Members" tier, I was supported by going to [https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe) and using the "Chat" feature in the lower right of the page... 

One of my questions to them was where to send other people (from the Forums) for support... I was told that I could tell others to go there for support problems. That will get you to a live person to help you.

They have access to your Ubuntu Pro account and can help you get things worked out.

We can only guide you in how it "should work" and point you in the right direction.

---

### Post by Holger_Gehrke on 2023-02-25
That doesn't look like an address from which I'd expect Canonical to deliver ESM-updates. Are you perhaps using the commercial variant of NGINX by F5 ? Then you'd get the updates for that from that address ...

For enabling the various Services associated with your Ubuntu Advantage contract you use the same command you used to get the status ('ubuntu-advantage' , 'ua', or 'pro') with the enable command followed by the name of the service you want to enable for example 'ua enable esm-infra'.

Holger

---

### Post by ubfan1 on 2023-02-25
How's your local connection?  I have noticed a 14.04 ESM (free) update stopped working after a bit with a really slow/flakey wireless, but did succeed after moving the machine closer to the router.

---

