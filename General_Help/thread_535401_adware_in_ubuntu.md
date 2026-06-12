---
title: "adware in ubuntu?"
date: 2007-08-26
forum: General Help
---

### Post by Pablopcv on 2007-08-26
hi. I'm having an adware issue what its very uncommon since i'm using ubuntu edgy. When I try to enter to any site (eg: google, yahoo, whatever) i'm redirected to a page with adds and no real info in the page source or in the page information. I tracked the source and its from this guys adserving.cpxinteractive.com.

I googled it and its seems like some windows users have this problem too and they fix it running something to remove it... but I have no clue how to get rid of this in ubuntu. I tried removing private info, blocking the site editing hosts and hosts.deny and connecting to a different isp but didnt work.

Im using:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20070601 Firefox/2.0.0.4 (Swiftfox) 
Ubuntu 6.10 edgy 


thanks
pcv

---

### Post by r4ik on 2007-08-26
Can't you blacklist the site ?

sudo gedit /etc/modprobe.d/blacklist

##nameofthesite

---

### Post by Pablopcv on 2007-08-26
thanks for your reply

I thought that blacklist was only for drivers and devices... anyway, that didnt worked...

---

### Post by r4ik on 2007-08-26
> **Pablopcv said:**
> thanks for your reply

I thought that blacklist was only for drivers and devices... anyway, that didnt worked...

I think you're right my bad.

---

### Post by moore.bryan on 2007-08-26
[I]what's the site to which you are redirected? 

have you emptied your cache and cookies?
[/I]

---

### Post by r4ik on 2007-08-26
This one looks better,

[http://ubuntuforums.org/showthread.php?t=241460](http://ubuntuforums.org/showthread.php?t=241460)

Good luck.

---

### Post by Pablopcv on 2007-08-26
yes as I said in my first post, I cleared my cache and modified hosts and didn't work. :confused:

---

### Post by Steveway on 2007-08-26
Did you try if this problem is still there if you use another OS or the LiveCD?
If yes then there seems to be a problem in your router or at your ISP and not at your PC.

---

### Post by Pablopcv on 2007-08-26
yes I tried with opera and normal Mozilla and its the same. I have 2 different internet connections of two different ISPs with different routers and still the same. The problem didn't appeared when I checked with windows.

Its clearly Ubuntu's problem.

---

### Post by Steveway on 2007-08-26
No!
Don't just try another browser, another OS!
Use the LiveCD or whatever you have and try it out.
EDIT: Sorry didn't read your whole Post. Well then your right something in you Ubuntu setup is wrong.
Can you posts your hosts file?

---

### Post by r4ik on 2007-08-26
From the terminal,

sudo gedit /etc/hosts

---

### Post by Pablopcv on 2007-08-26
of course:

```
127.0.0.1	localhost
127.0.1.1	pcv-laptop
127.0.0.1       localhost


# [Misc A - Z]
127.0.0.1  ad.a8.net
127.0.0.1  adserving.cpxinteractive.com
127.0.0.1  asy.a8ww.net
127.0.0.1  [www.aaa-livedoor.net](www.aaa-livedoor.net) #[Trojan-PSW.Win32.Maran.ei]
127.0.0.1  [www.abcsearcher.com](www.abcsearcher.com) #[Spamdexing][Microsoft.Strider]
127.0.0.1  abc-search.info
127.0.0.1  abloga.info #[Spamdexing]
127.0.0.1  [www.abx4.com](www.abx4.com) #[Adware.ABXToolbar]
127.0.0.1  acezip.net #[SiteAdvisor.acezip.net]
127.0.0.1  [www.acezip.net](www.acezip.net) #[Win32/Adware.180Solutions]
127.0.0.1  phpadsnew.abac.com
127.0.0.1  a.abnad.net
127.0.0.1  b.abnad.net
127.0.0.1  c.abnad.net #[eTrust.Tracking.Cookie]
127.0.0.1  d.abnad.net
127.0.0.1  e.abnad.net
127.0.0.1  t.abnad.net
127.0.0.1  adv.abv.bg
127.0.0.1  bimg.abv.bg
127.0.0.1  www2.a-counter.kiev.ua
127.0.0.1  accuserveadsystem.com
127.0.0.1  [www.accuserveadsystem.com](www.accuserveadsystem.com)
127.0.0.1  gtcc1.acecounter.com
127.0.0.1  gtp1.acecounter.com #[eTrust.Tracking.Cookie]
127.0.0.1  acestats.com
127.0.0.1  [www.acestats.com](www.acestats.com)
127.0.0.1  ads.active.com
127.0.0.1  am1.activemeter.com
127.0.0.1  [www.activemeter.com](www.activemeter.com) #[eTrust.Tracking.Cookie]
127.0.0.1  ads.activepower.net
127.0.0.1  stat.active24stats.nl #[eTrust.Tracking.Cookie]
127.0.0.1  at.ad2click.nl
127.0.0.1  cms.ad2click.nl
127.0.0.1  banner.ad.nu
127.0.0.1  ad-up.com
127.0.0.1  [www.ad-up.com](www.ad-up.com)
127.0.0.1  [www.adagencypro.com](www.adagencypro.com)
127.0.0.1  ad.pop1.adbn.ru
127.0.0.1  adserv.adbonus.com
127.0.0.1  [www.adbonus.com](www.adbonus.com)
127.0.0.1  james.adbutler.de #[Tenebril.TrackingCookie]
127.0.0.1  [www.adbutler.de](www.adbutler.de) #[SunBelt.AdButler.de]
127.0.0.1  adcp.adcentriconline.com
127.0.0.1  bell.adcentriconline.com #[Wildcard DNS]
127.0.0.1  media.adcentriconline.com
127.0.0.1  publicis.adcentriconline.com
127.0.0.1  adcomplete.com
127.0.0.1  [www.adcomplete.com](www.adcomplete.com)
127.0.0.1  [www.adcopy.info](www.adcopy.info)
127.0.0.1  axa.addcontrol.net #[Ewido.TrackingCookie.Addcontrol]
127.0.0.1  ads.addynamix.com #[SpySweeper.Spy.Cookie]
127.0.0.1  e13.media.addynamix.com
127.0.0.1  [www.adeos.eu](www.adeos.eu)
127.0.0.1  adcode.adengage.com
127.0.0.1  stats2.adengage.com
127.0.0.1  [www.adengage.com](www.adengage.com)
127.0.0.1  pt.server1.adexit.com
127.0.0.1  [www.adexit.com](www.adexit.com)
127.0.0.1  [www.ad4ever.com](www.ad4ever.com)
127.0.0.1  track.adform.net
127.0.0.1  [www.adfusion.com](www.adfusion.com)
127.0.0.1  harvest.adgardener.com
127.0.0.1  harvest6.adgardener.com
127.0.0.1  harvest7.adgardener.com
127.0.0.1  harvest8.adgardener.com
127.0.0.1  harvest11.adgardener.com
127.0.0.1  harvest12.adgardener.com
127.0.0.1  harvest13.adgardener.com
127.0.0.1  harvest163.adgardener.com
127.0.0.1  harvest176.adgardener.com
127.0.0.1  seeds.adgardener.com
127.0.0.1  [www.adgroups.net](www.adgroups.net)
127.0.0.1  [www.ad-groups.com](www.ad-groups.com) #[Ban Man Pro Banner Code]
127.0.0.1  [www.adgauge.com](www.adgauge.com)
127.0.0.1  host1.adhese.be #[Adhese Datamine Tag]
127.0.0.1  host2.adhese.be
127.0.0.1  host3.adhese.be #[ad.be.doubleclick.net]
127.0.0.1  host4.adhese.be
127.0.0.1  ssl3.adhost.com
127.0.0.1  www2.adhost.com
127.0.0.1  ads.adhostingsolutions.com #[eTrust.Tracking.Cookie]
127.0.0.1  [www.adimpact.com](www.adimpact.com)
127.0.0.1  [www.adinventoryrecorder.com](www.adinventoryrecorder.com)
127.0.0.1  adfarm1.adition.com
127.0.0.1  imagesrv.adition.com
127.0.0.1  ad.adition.net
127.0.0.1  adsearch.adkontekst.pl
127.0.0.1  community.adlandpro.com #[Ad-Aware Tracking.Cookie]
127.0.0.1  pk.adlandpro.com
127.0.0.1  te.adlandpro.com #[eTrust.Tracking.Cookie]
127.0.0.1  trafficex.adlandpro.com
127.0.0.1  [www.adlandpro.com](www.adlandpro.com) #[Ad-Aware Tracking.Cookie]
127.0.0.1  engine.adland.ru #[eTrust.Tracking.Cookie]
127.0.0.1  publicidad.adlead.com
127.0.0.1  ad.adlegend.com #[affects Webroot AlertNet]
127.0.0.1  media.adlegend.com #[eTrust.Tracking.Cookie]
127.0.0.1  [www.adlimg03.com](www.adlimg03.com)
127.0.0.1  classic.adlink.de
127.0.0.1  regio.adlink.de
127.0.0.1  west.adlink.de
127.0.0.1  rc.de.adlink.net #[eTrust.Tracking.Cookie]
127.0.0.1  tr.de.adlink.net
127.0.0.1  ads3.adman.gr #[eTrust.Tracking.Cookie]
127.0.0.1  r2d2.adman.gr
127.0.0.1  [www.adminder.com](www.adminder.com) #[SpySweeper.Spy.Cookie]
127.0.0.1  rms.admeta.com #[admeta.basefarm.net][eTrust.Tracking.Cookie]
127.0.0.1  ads.admodus.com #[eTrust.Tracking.Cookie]
127.0.0.1  ad.adnet.biz #[eTrust.Tracking.Cookie]
127.0.0.1  engine.adnet.ru
127.0.0.1  ad2.adnetinteractive.com
127.0.0.1  ad.adnetwork.com.br
127.0.0.1  [www.adnetworkonline.com](www.adnetworkonline.com)
127.0.0.1  s1.ad.adocean.pl #[Ewido.Tracking.Cookie]
127.0.0.1  s2.ad.adocean.pl
127.0.0.1  s1.centrumcz.adocean.pl #[eTrust.Tracking.Cookie]
127.0.0.1  s1.czgde.adocean.pl
127.0.0.1  s1.skgde.adocean.pl
127.0.0.1  ad01.adonspot.com
127.0.0.1  ad02.adonspot.com
127.0.0.1  isohunt.adonspot.com
127.0.0.1  ab.adpro.com.ua
127.0.0.1  ac.adpro.com.ua
127.0.0.1  system.adquick.nl
127.0.0.1  [www.adquest.nl](www.adquest.nl)
127.0.0.1  adreactor.com
127.0.0.1  adserver.adreactor.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  adx.adrenaline.cz
127.0.0.1  [www.adsforindians.com](www.adsforindians.com)
127.0.0.1  ad.adrefer.net
127.0.0.1  [www.adreporting.com](www.adreporting.com) #[SunBelt.Adreporting.com]
127.0.0.1  gambling911.adrevolver.com
127.0.0.1  media.adrevolver.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  track.adrevolver.com #[McAfee.Cookie-Adrevolver]
127.0.0.1  cntr.adrime.com
127.0.0.1  images.adrime.com
127.0.0.1  ad.adriver.ru
127.0.0.1  [www.adrotate.net](www.adrotate.net)
127.0.0.1  serv.ad-rotator.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ad.ads8.com
127.0.0.1  vip.ads8.com
127.0.0.1  [www.ads183.com](www.ads183.com)
127.0.0.1  antevenio.flux.ads-click.com
127.0.0.1  ad.ads.dk
127.0.0.1  tdkads.ads.dk
127.0.0.1  adservercentral.com
127.0.0.1  banners.adservercentral.com
127.0.0.1  [www.adservercentral.com](www.adservercentral.com) #[SunBelt.adservercentral.com]
127.0.0.1  adservicedomain.info
127.0.0.1  adsfac.net #[Facilitate Tracking Code]
127.0.0.1  images.adshuffle.com
127.0.0.1  this.content.served.by.adshuffle.com
127.0.0.1  ad-soft.net #[regfreeze.net]
127.0.0.1  adsaway.com #[HTML/TrojanDownloader.Agent.BP trojan]
127.0.0.1  www.adsaway.com #[Google.Warning]
127.0.0.1  www.adshot.de
127.0.0.1  allchix.adsmax.com
127.0.0.1  www2.adsmax.com
127.0.0.1  www.adsodainteractive.com
127.0.0.1  37.adsonar.com
127.0.0.1  ads.adsonar.com
127.0.0.1  foxnews.adsonar.com
127.0.0.1  js.adsonar.com
127.0.0.1  redir.adsonar.com
127.0.0.1  www.adspace.be
127.0.0.1  g.adspeed.net
127.0.0.1  serv.adspeed.com
127.0.0.1  ads.adsponse.de
127.0.0.1  creative.adsrevenue.net
127.0.0.1  popunder.adsrevenue.net
127.0.0.1  adserve.adster.com
127.0.0.1  images.adster.com
127.0.0.1  adsvert.com
127.0.0.1  o.adtargeter.com
127.0.0.1  ads.adtiger.de
127.0.0.1  www.adtiger.de
127.0.0.1  ads.adgoto.com
127.0.0.1  adsrv.admindshare.com
127.0.0.1  adtology.com
127.0.0.1  adtology2.com
127.0.0.1  ad.adtoma.com
127.0.0.1  downldcl.adtoolsinc.com
127.0.0.1  www.adtoolsinc.com
127.0.0.1  www.adtrade.net
127.0.0.1  www.adtrader.com
127.0.0.1  netshelter.adtrix.com
127.0.0.1  ads.advancedpcmedia.com
127.0.0.1  survey.advantageresearch.com
127.0.0.1  ad.adver.com.tw
127.0.0.1  www.adventideas.com #[Adcycle]
127.0.0.1  www.adversal.com
127.0.0.1  www.adversalservers.com
127.0.0.1  austria1.adverserve.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ads.advertise.net
127.0.0.1  www.advertisingspaces.net
127.0.0.1  www.advertisingstats.com
127.0.0.1  advertisingpurchase.com
127.0.0.1  ad.adverticum.net
127.0.0.1  img.adverticum.net
127.0.0.1  imgs.adverticum.net
127.0.0.1  ads.advertisingz.com
127.0.0.1  ad.advertstream.com
127.0.0.1  adviva.com #[IE-SpyAd]
127.0.0.1  www.adviva.com
127.0.0.1  ads.adviva.net #[Panda.Spyware:Cookie/Adviva]
127.0.0.1  de.ads.adviva.net
127.0.0.1  adstats.adviva.net
127.0.0.1  www.traf.advscripts.com
127.0.0.1  ad.adworx.at
127.0.0.1  www.ad-z.de
127.0.0.1  banners.adzones.com
127.0.0.1  clicks.adzones.com
127.0.0.1  feeds.adzones.com
127.0.0.1  www.adzones.com
127.0.0.1  aeoworld.de
127.0.0.1  www.aeoworld.de #[W32/WMF-exploit]
127.0.0.1  banners.affilimatch.de
127.0.0.1  tracker.affistats.com #[msvrl.dll]
127.0.0.1  adz.afterdawn.net
127.0.0.1  ad.afy11.net
127.0.0.1  stats.agent.co.il
127.0.0.1  agentmediagroup.com #[Javascript.Exploit]
127.0.0.1  www.agentmediagroup.com
127.0.0.1  rmbannerserver.agestado.com.br
127.0.0.1  stats.agentinteractive.com
127.0.0.1  api.aggregateknowledge.com
127.0.0.1  aams1.aim4media.com
127.0.0.1  artwork.aim4media.com
127.0.0.1  www.aim4media.com #[SunBelt.Adserver.aim4media]
127.0.0.1  adlik.akavita.com
127.0.0.1  adlik2.akavita.com
127.0.0.1  adserver.akqa.net #[Ad-Aware Tracking.Cookie]
127.0.0.1  www.alaqiq.net #[Javascript.Exploit]
127.0.0.1  download.alexa.com #[Trackware.Alexa][SPYW_ALEXA.A]
127.0.0.1  download.china.alibaba.com #[Adware.AlibabaTB][AdWare.ToolBar.Alibabar.b]
127.0.0.1  tracking.allposters.com
127.0.0.1  ad.allstar.cz
127.0.0.1  bokee.allyes.com
127.0.0.1  demoafp.allyes.com
127.0.0.1  eastmoney.allyes.com
127.0.0.1  smarttrade.allyes.com
127.0.0.1  taobaoafp.allyes.com
127.0.0.1  tom.allyes.com
127.0.0.1  uuseeafp.allyes.com
127.0.0.1  www.almondnetworks.com
127.0.0.1  www.almoso3h.com #[Trojan-PSW.Win32.VB.cl]
127.0.0.1  www.alsaloumainvestment.com #[Win32/SpamTool.Gadina]
127.0.0.1  ad.altervista.org
127.0.0.1  marx2.altervista.org
127.0.0.1  pqwaker.altervista.org
127.0.0.1  bantam.ai.net
127.0.0.1  fiona.ai.net
127.0.0.1  adimg.alice.it
127.0.0.1  adv.alice.it
127.0.0.1  count1.altastat.com
127.0.0.1  altmedia101.com
127.0.0.1  www.alldep.com #[Spamdexing]
127.0.0.1  adserver.alt.com
127.0.0.1  c0.amazingcounters.com
127.0.0.1  c1.amazingcounters.com
127.0.0.1  c2.amazingcounters.com
127.0.0.1  c3.amazingcounters.com
127.0.0.1  c4.amazingcounters.com
127.0.0.1  c5.amazingcounters.com
127.0.0.1  c6.amazingcounters.com
127.0.0.1  c7.amazingcounters.com
127.0.0.1  c8.amazingcounters.com
127.0.0.1  www.amazingcounters.com
127.0.0.1  banner.ambercoastcasino.com
127.0.0.1  ads.amdmb.com
127.0.0.1  whos.amung.us #[WebBug]
127.0.0.1  advert.ananzi.co.za
127.0.0.1  advert2.ananzi.co.za
127.0.0.1  adserver.ancestry.com #[RealMedia]
127.0.0.1  adserver04.ancestry.com #[RealMedia]
127.0.0.1  andishecenter.com #[VBS/Envary.A]
127.0.0.1  www.andyhoppe.com
127.0.0.1  angpeu.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  ads.angryape.com
127.0.0.1  banners.ads.angryape.com
127.0.0.1  www.antarasystems.com
127.0.0.1  www.anticlown.com
127.0.0.1  ads.antionline.com
127.0.0.1  junior.apk.net
127.0.0.1  www.arcadebanners.com
127.0.0.1  www.arcadebannerexchange.com
127.0.0.1  ard114.info #[Spamdexing]
127.0.0.1  areabuyreal.com
127.0.0.1  act.areabuyreal.com #[Win32/TrojanDownloader.Zlob]
127.0.0.1  click.areabuyreal.com #[WildCard DNS]
127.0.0.1  www.areabuyreal.com
127.0.0.1  demiurge.arstechnica.com
127.0.0.1  artsklimited.info #[Win32/Padodor.NAQ]
127.0.0.1  banner.arttoday.com
127.0.0.1  ads.asia1.com.sg
127.0.0.1  asimpleinternet.com #[Tenebril.SpecialOffers]
127.0.0.1  www.asimpleinternet.com
127.0.0.1  ads.ask.com #[sv-click.looksmart.com]
127.0.0.1  www.askyaya.com #[SunBelt.AskYaya]
127.0.0.1  ads.aspalliance.com
127.0.0.1  ads.associatedcontent.com
127.0.0.1  dist.atlas-ia.com #[ADW_ATLAST.A]
127.0.0.1  www.atlas-ia.com #[Adware.OfferAgent][Adware-Atlas]
127.0.0.1  elitegaming.ath.cx #[Adware.AdSupport]
127.0.0.1  www.elitegaming.ath.cx
127.0.0.1  ads.auctionads.com
127.0.0.1  audiogalaxy.com
127.0.0.1  www.audiogalaxy.com
127.0.0.1  auto-search.org #[VicMan Search]
127.0.0.1  ads.auctioncity.co.nz
127.0.0.1  www.autosurfpro.com
127.0.0.1  ads.autotrader.co.za
127.0.0.1  adserving.autotrader.com #[SunBelt.AdServing.AutoTrader.com]
127.0.0.1  www.axill.com
127.0.0.1  images.axill.in
127.0.0.1  www.axill.in
127.0.0.1  axload.to #[Adware.Webprefix][Trojan.Downloader.6588.E]
127.0.0.1  valid.axload.to
127.0.0.1  ayiosamvrosios.com #[Javascript.Exploit]
127.0.0.1  www.azads.net
127.0.0.1  azresults.com #[Spamdexing]
127.0.0.1  www.azresults.com
127.0.0.1  azsearch.org
# [B]
127.0.0.1  babla.info #[Spamdexing]
127.0.0.1  adserver1.backbeatmedia.com
127.0.0.1  adserver1-images.backbeatmedia.com
127.0.0.1  bullseye.backbeatmedia.com
127.0.0.1  www.badhyip.org #[Google.Warning]
127.0.0.1  ads.badische-zeitung.de
127.0.0.1  bar.baidu.com #[Win32/Adware.Toolbar.Baidu][Sophos.JS/BDHelper-A]
127.0.0.1  download.baigoo.com #[AdWare.Win32.Baigoo.a][Trackware.Baigoo]
127.0.0.1  ad.baiso.com.cn #[Trojan.Baiso][ADSPY/BaiduBar.P]
127.0.0.1  balticaffiliate.com #[Spamdexing]
127.0.0.1  www.baltictop.com
127.0.0.1  adsrv.bankrate.com
127.0.0.1  click.banneradv.com
127.0.0.1  adserver.banneradministration.com
127.0.0.1  www.bannerbox.cn
127.0.0.1  bannerboxes.com #[BannerBoxes Ad Code]
127.0.0.1  clicks.bannerboxes.com
127.0.0.1  feeds.bannerboxes.com
127.0.0.1  www.bannerboxes.com
127.0.0.1  bannerbg.com
127.0.0.1  www.banner-exchange.nl
127.0.0.1  ad.bannerhost.ru
127.0.0.1  banners.bannerlandia.com.ar
127.0.0.1  www.bannermanagement.nl
127.0.0.1  www.bannerout.com
127.0.0.1  www.banneroverdrive.com
127.0.0.1  www.bannerpromotion.it
127.0.0.1  www.banner-mania.com
127.0.0.1  www.bannerspace.com
127.0.0.1  www3.bannerspace.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www5.bannerspace.com
127.0.0.1  www6.bannerspace.com
127.0.0.1  www7.bannerspace.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.bannerswap.ca
127.0.0.1  ads.vg.basefarm.net #[RealMedia]
127.0.0.1  media.baventures.com
127.0.0.1  ads.baz.ch
127.0.0.1  ad2.bbmedia.cz
127.0.0.1  bbeplayer.com #[WebBug]
127.0.0.1  bc0.cn #[ANI.Exploit]
127.0.0.1  autocontext.begun.ru
127.0.0.1  adlogger.bertgeens.be
127.0.0.1  www.belstat.be
127.0.0.1  www.belstat.com
127.0.0.1  www.belstat.nl
127.0.0.1  oas.benchmark.fr #[RealMedia]
127.0.0.1  bengilani.com #[VBS/Envary.A]
127.0.0.1  bestinfosearch.com
127.0.0.1  www.bestinfosearch.com #[Malicious.Links]
127.0.0.1  bestinshowjewelry.com #[HTML/TrojanDownloader.Agent.BP]
127.0.0.1  www.bestinshowjewelry.com
127.0.0.1  webtrends.besite.be
127.0.0.1  www.besttoolbars.net #[ADW_TBARWIN32.A]
127.0.0.1  ads.betanews.com
127.0.0.1  banner.betfred.com
127.0.0.1  www.bettertextads.com
127.0.0.1  big4top.com
127.0.0.1  www.big4top.com #[IFrame.Exploit]
127.0.0.1  ad0.bigmir.net
127.0.0.1  ad1.bigmir.net
127.0.0.1  ad4.bigmir.net
127.0.0.1  ad5.bigmir.net
127.0.0.1  ad6.bigmir.net
127.0.0.1  ad7.bigmir.net
127.0.0.1  adi.bigmir.net
127.0.0.1  c.bigmir.net #[SecuritySpace.WebBug]
127.0.0.1  i.bigmir.net
127.0.0.1  bigtracker.com
127.0.0.1  bighits.net
127.0.0.1  bigticker.bighits.net
127.0.0.1  bounty.bighits.net
127.0.0.1  www.bighits.net
127.0.0.1  counter.bigli.ru
127.0.0.1  banex.bikers-engine.com
127.0.0.1  ad2.billboard.cz
127.0.0.1  adserver.bizhat.com
127.0.0.1  counter.bizland.com
127.0.0.1  dc.bizjournals.com
127.0.0.1  webads.bizservers.com
127.0.0.1  blackhatcrew.ru
127.0.0.1  www.black-hole.co.uk
127.0.0.1  ads2.blastro.com
127.0.0.1  ads3.blastro.com
127.0.0.1  ads4.blastro.com
127.0.0.1  blaze-search.com
127.0.0.1  ads.blick.ch
127.0.0.1  streamstats1.blinkx.com
127.0.0.1  ads.blizzard.com
127.0.0.1  blogadswap.com
127.0.0.1  tracker.blogbeat.net
127.0.0.1  ads.blogdrive.com
127.0.0.1  banners.blogexplosion.com
127.0.0.1  counter.blogexplosion.com
127.0.0.1  blogtextlinks.blogexplosion.com
127.0.0.1  rentblog.blogexplosion.com
127.0.0.1  mapstats.blogflux.com
127.0.0.1  www.blogpatrol.com
127.0.0.1  pcbutts1-therealtruth.blogspot.com
127.0.0.1  t.blogreaderproject.com #[WebBug]
127.0.0.1  ads1.prod.bluetape.com
127.0.0.1  blogmark.bokee.com #[Adware.BocaiToolbar]
127.0.0.1  count.blogscout.de
127.0.0.1  track.blogcounter.de
127.0.0.1  www.blogcounter.de
127.0.0.1  adserver.bluewin.ch
127.0.0.1  ads.boardtracker.com
127.0.0.1  ranks.boardtracker.com
127.0.0.1  adimage.bokee.com
127.0.0.1  ad.bol.bg
127.0.0.1  adv.bol.bg
127.0.0.1  ads.bomis.com
127.0.0.1  banners.bookmaker.com
127.0.0.1  boolom.com #[Win32/Viking.DA][server down?]
127.0.0.1  ccc.boolans.com #[Adware.Rugo]
127.0.0.1  err.boom.ru
127.0.0.1  www.borlander.cn #[Adware.Borlan]
127.0.0.1  www.borlander.com.cn #[ADSPY/Boran.X.19.C]
127.0.0.1  astalavista.box.sk #[SiteAdvisor.astalavista.box.sk]
127.0.0.1  ads.brainiads.com
127.0.0.1  download.bravesentry.com #[McAfee.BraveSentry]
127.0.0.1  support.bravesentry.com
127.0.0.1  www.bravesentry.com #[NOD32.Win32/Adware.SpySheriff.variant]
127.0.0.1  bans.bride.ru
127.0.0.1  cc.bridgetrack.com
127.0.0.1  citi.bridgetrack.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  citi.bridgetrack.com.edgesuite.net
127.0.0.1  rccl.bridgetrack.com #[MVPS.Criteria]
127.0.0.1  banners.broadwayworld.com
127.0.0.1  www.browserplugin.com #[HJTH.EroticAccess][wobz.de]
127.0.0.1  bsdpng.info
127.0.0.1  btbilgisayarkursu.com #[Win32/TrojanDownloader.Small.AWA]
127.0.0.1  www.btbilgisayarkursu.com #[Win32/TrojanDownloader.Small.AWA]
127.0.0.1  www.bulletads.com
127.0.0.1  redemption.bullseye-media.net
127.0.0.1  users.bullseye-media.net
127.0.0.1  www.bullseye-media.net
127.0.0.1  bunnezone.com #[Win32/Jep.Russ]
127.0.0.1  burnsrecyclinginc.com #[Win32/TrojanDropper.Agent.NBX]
127.0.0.1  www.burnsrecyclinginc.com
127.0.0.1  ad1.bustcash.com
127.0.0.1  www.buy404s.com
127.0.0.1  www.buzzclick.com
127.0.0.1  tr.buzzlogic.com
127.0.0.1  byindia.com #[Spamdexing]
127.0.0.1  www.byip.cn #[Google.Warning]
127.0.0.1  multi.byulcom.com #[Win32/TrojanDownloader.Small.BIV]
# [C]
127.0.0.1  ads.calgarystampede.com
127.0.0.1  canadianhw.ca #[VBS/Envary.A]
127.0.0.1  www.canadianhw.ca
127.0.0.1  ads.capablenet.com
127.0.0.1  images.cashfiesta.com #[AdWare.CashFiesta.a]
127.0.0.1  www.cashfiesta.com #[McAfee.Adware-CashFiesta]
127.0.0.1  www.cashfiesta.net
127.0.0.1  banner.casinoking.com #[AdWare.Win32.Casino.ae]
127.0.0.1  www.cashventure.com
127.0.0.1  ads.casino.com
127.0.0.1  out.catchonlife.com #[lootseek.com][server down?]
127.0.0.1  ad.caradisiac.com
127.0.0.1  ads.cars.com
127.0.0.1  blockbuster.com.7.ccg360.com
127.0.0.1  blockbuster.med.ccg360.com
127.0.0.1  www.cd321.com
127.0.0.1  ads.cdfreaks.com #[eTrust.Ads.cdfreaks]
127.0.0.1  ads.cdrinfo.com
127.0.0.1  stats.cdrinfo.com #[WebBug]
127.0.0.1  www.celebritypicturesarchive.com #[Trojan-Downloader.Win32.IstBar.nn]
127.0.0.1  www.celebrity-pictures-world.com #[Trojan-Downloader.Win32.IstBar.nn]
127.0.0.1  clicktracker.centrum.cz
127.0.0.1  mds.centrport.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  cetrk.com
127.0.0.1  cesp.be #[HTML/TrojanDownloader.Agent.NAB]
127.0.0.1  adserver.cducinema.com
127.0.0.1  counter.cgiworld.net
127.0.0.1  tracker.cgiworld.net
127.0.0.1  abc.checkm8.com
127.0.0.1  rmm1u.checkm8.com
127.0.0.1  web.checkm8.com #[CHECKM8 AD TAGS]
127.0.0.1  web2.checkm8.com
127.0.0.1  ads.checkm8.co.za
127.0.0.1  ads.chellomedia.com
127.0.0.1  ads.china.com
127.0.0.1  www.china3q.com #[Trojan.Startpage.S]
127.0.0.1  ad.chip.de
127.0.0.1  www.chsniper.com #[Downloader.Sniper]
127.0.0.1  ad.cibleclick.com #[eTrust.Cibleclick]
127.0.0.1  www.cibleclick.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  cindyproject.info #[Spamdexing]
127.0.0.1  www.classicequipment.com #[Google.Warning]
127.0.0.1  board.classifieds1000.com
127.0.0.1  xp.classifieds1000.com
127.0.0.1  www.classifieds1000.com #[SiteAdvisor.classifieds1000.com]
127.0.0.1  images.clckm.com
127.0.0.1  pics.clckm.com #[Parking Service]
127.0.0.1  cleanfeed.info #[Spamdexing]
127.0.0.1  ads.clickad.com #[eTrust.Tracking.Cookie]
127.0.0.1  clickbank.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  hop.clickbank.net #[Adware.Clickbank][Adware.ClickDLoader]
127.0.0.1  ssl.clickbank.net
127.0.0.1  zzz.clickbank.net #[Ewido.TrackingCookie.Clickbank]
127.0.0.1  publishers.clickbooth.com #[directleads.com]
127.0.0.1  clickboothlnk.com
127.0.0.1  www.clickboothlnk.com
127.0.0.1  j.clickdensity.com
127.0.0.1  r.clickdensity.com
127.0.0.1  dsml.clickexperts.net
127.0.0.1  www.clicks2you.com
127.0.0.1  www.clickmanage.com
127.0.0.1  clicktopsite.com #[Spamdexing]
127.0.0.1  clicktracks.com #[McAfee.Cookie-Clicktracks]
127.0.0.1  stats.clicktracks.com #[Tenebril.Tracking.Cookie]
127.0.0.1  stats1.clicktracks.com # [eTrust.Tracking.Cookie]
127.0.0.1  stats2.clicktracks.com #[SpySweeper.Spy.Cookie]
127.0.0.1  stats3.clicktracks.com
127.0.0.1  stats4.clicktracks.com
127.0.0.1  www.clicktracks.com #[SunBelt.ClickTracks]
127.0.0.1  www.is1.clixgalore.com
127.0.0.1  www.clixgalore.com
127.0.0.1  hit.click2006.com
127.0.0.1  www2.click-fr.com
127.0.0.1  www3.click-fr.com
127.0.0.1  www4.click-fr.com
127.0.0.1  www.clickhouse.com #[SunBelt.ClickHouse]
127.0.0.1  www.click-power.com #[Win32/TrojanDownloader.VB.JL][Win32.Virtumonde.by]
127.0.0.1  www.clicks4u.com
127.0.0.1  www.clicksbroker.com
127.0.0.1  ad1.clickhype.com #[Ewido.TrackingCookie.Clickhype]
127.0.0.1  clickoly.com #[Spamdexing]
127.0.0.1  redirect.clickshield.net
127.0.0.1  clickthru.net
127.0.0.1  ads.clickthru.net
127.0.0.1  icon.clickthru.net
127.0.0.1  clicktorrent.info
127.0.0.1  static.clicktorrent.info
127.0.0.1  www.clicktorrent.info #[phpAds]
127.0.0.1  www1.clicktorrent.info
127.0.0.1  norbert_sirot.club.fr #[Trojan-Spy.Win32.Banker.anv]
127.0.0.1  banner.clubdicecasino.com
127.0.0.1  adserver.clix.pt
127.0.0.1  ad.cmfu.com
127.0.0.1  www.cnstats.com
127.0.0.1  ad.coas2.co.kr
127.0.0.1  ads.cobrad.com
127.0.0.1  collectiveads.net
127.0.0.1  www.combimedia.nl
127.0.0.1  bdx.comclick.com
127.0.0.1  br.comclick.com
127.0.0.1  ct2.comclick.com #[Tenebril.Tracking.Cookie]
127.0.0.1  fl01.ct2.comclick.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ihm01.ct2.comclick.com
127.0.0.1  www.comclick.com #[Ewido.TrackingCookie.Comclick]
127.0.0.1  members.commissionmonster.com
127.0.0.1  aa.connextra.com
127.0.0.1  bb.connextra.com #[a22.g.akamai.net]
127.0.0.1  cc.connextra.com
127.0.0.1  dd.connextra.com
127.0.0.1  ee.connextra.com
127.0.0.1  ff.connextra.com #[a22.g.akamai.net]
127.0.0.1  data.connextra.com
127.0.0.1  linkexchange.consoleunderground.com
127.0.0.1  www.consoleunderground.com #[Adware.Begin2search]
127.0.0.1  ads.consumeraffairs.com
127.0.0.1  ads.contactmusic.com #[AdvertPro]
127.0.0.1  servedby.contextuad.org
127.0.0.1  svp.contextuad.org #[SunBelt.ContextuAd]
127.0.0.1  www.contextualclick.com #[Dynamic keywords analyser]
127.0.0.1  ads.console.net
127.0.0.1  su.copylouis.info #[SiteAdvisor.msiesettings.com]
127.0.0.1  banners.copyscape.com
127.0.0.1  www.countit.ch
127.0.0.1  counter.co.kz
127.0.0.1  www.counter-gratis.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.countercentral.com
127.0.0.1  www.counterguide.com
127.0.0.1  counter-shop.net
127.0.0.1  htm-pop-ky.counterstat.net
127.0.0.1  www.counting4free.com
127.0.0.1  www.counter.cz
127.0.0.1  www.counti.de
127.0.0.1  www.countmypage.com
127.0.0.1  log1.countomat.com
127.0.0.1  connectionzone.com
127.0.0.1  www.couponsandoffers.com #[Adware.TopMoxie]
127.0.0.1  data.coremetrics.com
127.0.0.1  test.coremetrics.com #[SpySweeper.Spy.Cookie]
127.0.0.1  twci.coremetrics.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  banner.coza.com
127.0.0.1  www.cpaclicks.com #[Spamdexing]
127.0.0.1  server.cpmstar.com #[ads.shizmoo.com]
127.0.0.1  cracks.am #[eTrust.Cracks.am][ADW_CRAMTB.A]
127.0.0.1  www.cracks.am #[****-portal.com][Adware.CramToolbar]
127.0.0.1  ads.cracked.com
127.0.0.1  track.cracked.com
127.0.0.1  www.crackserver.com #[StopBadware.Report]
127.0.0.1  new.crashextads.co.uk
127.0.0.1  crawl.ws
127.0.0.1  cont.crawl.ws #[AdWare.Win32.MegaKiss.b]
127.0.0.1  www.crawl.ws
127.0.0.1  counter.credo.ru
127.0.0.1  www.cridem.org #[Win32/Spy.Banker.AHY]
127.0.0.1  www.crispads.com
127.0.0.1  ads.crosswinds.net
127.0.0.1  megabyte.crosswinds.net #[server down?]
127.0.0.1  ads.crucialparadigm.com
127.0.0.1  crunet.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  cxss358.com #[HTML/TrojanDownloader.Agent.BP]
127.0.0.1  cyberbounty.com
127.0.0.1  clk.cyberbounty.com
127.0.0.1  pop.cyberbounty.com
127.0.0.1  serve.cyberbounty.com
127.0.0.1  www.cyberbounty.com
127.0.0.1  js.cybermonitor.com #[McAfee.Cookie-Cybermonitor]
127.0.0.1  stat3.cybermonitor.com
127.0.0.1  banner.cybertechdev.com
127.0.0.1  cybertown.ru
127.0.0.1  search.cygo.net
127.0.0.1  www.cygo.net #[McAfee.Adware-Cygo]
127.0.0.1  cytron.com #[DailyWinner][eTrust.Cytron]
127.0.0.1  www.cytron.com
# [D]
127.0.0.1  www.d3m0n.biz
127.0.0.1  dabestdomain.info #[SiteAdvisor.msiesettings.com]
127.0.0.1  ads.dada.it
127.0.0.1  www.dailykeys.com #[Google.Warning]
127.0.0.1  mm.dalumm.com #[Win32/TrojanDownloader.Small.TZ]
127.0.0.1  www.data-jpn.com #[Trojan.Pajatan]
127.0.0.1  banner.date.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.dateclix.com #[DateClix.com Banner Exchange Code]
127.0.0.1  datingbanners.net
127.0.0.1  ads.datinggold.com
127.0.0.1  ad.db3nf.com
127.0.0.1  dcstat.com
127.0.0.1  deansplanet.com #[Malicious.Links.Zango]
127.0.0.1  www.deansplanet.com
127.0.0.1  au.track.decideinteractive.com
127.0.0.1  au.link.decideinteractive.com
127.0.0.1  eu.link.decideinteractive.com
127.0.0.1  link.decideinteractive.com
127.0.0.1  www.decideinteractive.com
127.0.0.1  www.decideinteractive.co.uk
127.0.0.1  deepcom.com #[SiteAdvisor.deepcom.com]
127.0.0.1  www.deepcom.com #[TrojanDropper.Win32.Small.gt]
127.0.0.1  collector.deepmetrix.com
127.0.0.1  geo.deepmetrix.com
127.0.0.1  www.deepmetrix.com #[Microsoft]
127.0.0.1  demsas-iran.com #[VBS/Envary.A]
127.0.0.1  ads.dennisnet.co.uk
127.0.0.1  ad.depositfiles.com
127.0.0.1  ad.detik.com
127.0.0.1  desire-search.com #[Spamdexing]
127.0.0.1  ads.deviantart.com
127.0.0.1  adsvr.deviantart.com
127.0.0.1  phpadsnew.devstart.com
127.0.0.1  banners.diariodelaltoaragon.es
127.0.0.1  track.did-it.com #[Panda.Spyware:Cookie/did-it]
127.0.0.1  counter.dieit.de
127.0.0.1  digiwexonline.com #[W32/Kibik.a]
127.0.0.1  www.digink.com #[PcTools.SysCheckBop32]
127.0.0.1  ads.digitalpoint.com
127.0.0.1  geo.digitalpoint.com
127.0.0.1  hk.digitaltrends.com
127.0.0.1  comm1.digits.com
127.0.0.1  counter.digits.com
127.0.0.1  ads.dir.bg
127.0.0.1  banners.dir.bg
127.0.0.1  ad.directaclick.com
127.0.0.1  direct-ip.com #[Adware-DirectIP][SecurityRisk.DirectIP]
127.0.0.1  www.direct-ip.com #[Adware-DirectIP][Adware-CommanderNET]
127.0.0.1  ad.directconnect.se
127.0.0.1  banners.directnic.com #[SecuritySpace.WebBug][MVPS.Criteria]
127.0.0.1  dnads.directnic.com
127.0.0.1  parked.directnic.com
127.0.0.1  stats.directnic.com
127.0.0.1  www.directnicparking.com
127.0.0.1  cache.directorym.com #[c2.mii.instacontent.net]
127.0.0.1  ads.directnetadvertising.net #[SiteAdvisor.directnetadvertising.net]
127.0.0.1  www.directnetadvertising.net #[Ad-Aware Tracking.Cookie]
127.0.0.1  ad.displayadsmedia.com
127.0.0.1  agentq.ditto.com
127.0.0.1  js.ditto.com
127.0.0.1  matrix.ditto.com
127.0.0.1  media.ditto.com #[a232.x.akamai.net]
127.0.0.1  www.ditto.com #[AdWare.Win32.Softomate.c]
127.0.0.1  cnads.dixcom.com
127.0.0.1  dcww.dmcast.com #[Adware-DesktopMedia]
127.0.0.1  ad1.dmcmedia.co.kr
127.0.0.1  dmdl.dmcast.com
127.0.0.1  install.dmcast.com #[Adware-DesktopMedia.dr]
127.0.0.1  track.dmipartners.com
127.0.0.1  ads.dmnews.com
127.0.0.1  ad.dmpi.net
127.0.0.1  ad2.dmpi.net
127.0.0.1  ad3.dmpi.net
127.0.0.1  ad4.dmpi.net
127.0.0.1  ubnm.dmpi.net
127.0.0.1  searchportal.dnparking.com #[Parking Service]
127.0.0.1  www.dnscaching.net #[SiteAdvisor.dnscaching.net]
127.0.0.1  dnv-counter.com
127.0.0.1  www.domamil.cz #[Trojan.Beagooz]
127.0.0.1  www.dodostats.com
127.0.0.1  dontouchmyad.com #[drivecleaner.com]
127.0.0.1  doorgen.com #[Spamdexing]
127.0.0.1  www.doorgen.com 
127.0.0.1  ads.dotomi.com
127.0.0.1  www.donotchangeme.com
127.0.0.1  www.down988.cn #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.download-services.com #[VBA32.Trojan-Downloader.Agent.26]
127.0.0.1  www.downseek.com #[SunBelt.DownSeek Search]
127.0.0.1  downloa-d.com
127.0.0.1  www.downloa-d.com #[Trojan-Clicker.Win32.Agent.ip]
127.0.0.1  banners.dpnet.com.br
127.0.0.1  drmx01.net #[Spamdexing]
127.0.0.1  counter.dreamhost.com
127.0.0.1  www.claus.drehteile-rieche.de #[Win32.Formglieder.B]
127.0.0.1  www.dreamadvert.com #[SunBelt.Dreamadvert]
127.0.0.1  www.dropthehammer.com #[Win32/Spy.Banker.AHY]
127.0.0.1  ads.drugs.com
127.0.0.1  b.ds1.nl
127.0.0.1  ddd.dudu.com #[Tenebril.DuDu Accelerator]
127.0.0.1  ulink4.dudu.com #[Adware.DDDClient][SunBelt.DuDuAccelerator]
127.0.0.1  ulink13.dudu.com #[Win32/Adware.DM]
127.0.0.1  www.dudu.com #[McAfee.Downloader-AVV]
127.0.0.1  www.duenow.com
127.0.0.1  www.dutty.de #[W32.Peerload.A]
127.0.0.1  gfx.dvlabs.com
127.0.0.1  klipads.dvlabs.com
127.0.0.1  www.dzy520.com #[Google.Warning]
# [E]
127.0.0.1  e2give.com #[Adware-E2Give][Spyware.e2give]
127.0.0.1  www.e2give.com
127.0.0.1  hits.e.cl
127.0.0.1  banners.earnunited.com
127.0.0.1  blogads.ebanner.nl
127.0.0.1  www.e-bannerx.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.earncashontheinternet.com #[SunBelt.OpinionBar]
127.0.0.1  www.eash.info #[Spamdexing][Microsoft.Strider]
127.0.0.1  click.easilyfound.com #[Tenebril.AdTraffic]
127.0.0.1  www.easilyfound.com
127.0.0.1  www.eastworldnetwork.com
127.0.0.1  www.easycounter.com
127.0.0.1  banners.easydns.com
127.0.0.1  easyerror.info #[Trojan-Downloader.Win32.Delf.agw]
127.0.0.1  easyhitcounters.com
127.0.0.1  beta.easyhitcounters.com
127.0.0.1  www.ebannertraffic.com
127.0.0.1  easy-web-stats.com
127.0.0.1  adserv1.ebates.com #[WebSavings]
127.0.0.1  mailer.ebates.com
127.0.0.1  www.ebates.com #[Adware.MoeMoney]
127.0.0.1  ads.eccentrix.com
127.0.0.1  ads.ecrush.com #[AdvertPro]
127.0.0.1  www.eden21.net #[Win32/Haxdoor][TR/Dldr.Botol.D.1]
127.0.0.1  c6.edgesuite.net #[RealMedia]
127.0.0.1  ads.edirectme.com
127.0.0.1  qq.ee28.cn #[Javascript.Exploit]
127.0.0.1  einfachstarten.com #[Trojan.Firpage]
127.0.0.1  www.ejmx.com #[Adware.ElectroJMX]
127.0.0.1  ad.e-kolay.net
127.0.0.1  www.ek21.com #[Trojan.Chost.B]
127.0.0.1  www.elancenet.org #[Worm/Eyeveg.CH]
127.0.0.1  elitwarez.ru #[Javascript.Exploit][server down?]
127.0.0.1  www.elitwarez.ru
127.0.0.1  now.eloqua.com #[WebBug]
127.0.0.1  ads.eluniversal.com.mx
127.0.0.1  hits.eluniversal.com.mx
127.0.0.1  publicidad.eluniversal.com.mx
127.0.0.1  elwebsearch.info #[Malicious Links.Umax]
127.0.0.1  wwv.elwebsearch.info
127.0.0.1  www.elwebsearch.info
127.0.0.1  ad1.emediate.dk
127.0.0.1  ad1.emediate.se
127.0.0.1  www.emoinstaller.com #[Win32/Adware.NdotNet][SiteAdvisor.emoinstaller.com]
127.0.0.1  www.emusic.com #[McAfee.Adware-eMusic][F-Secure.Adware.eMusic]
127.0.0.1  dotnet.endai.com
127.0.0.1  stats.engineseeker.com
127.0.0.1  entk.net
127.0.0.1  log.enquisite.com
127.0.0.1  adv.entercasino.com #[Adware.Casino.V]
127.0.0.1  ads.eog.com
127.0.0.1  ads.e-planning.net
127.0.0.1  ads.us.e-planning.net
127.0.0.1  adserving00.epi.es
127.0.0.1  adserving03.epi.es
127.0.0.1  launcheruk.escritorioactivo.com
127.0.0.1  vipuk.escritorioactivo.com #[HJTH.123Messenger Hijacker]
127.0.0.1  www.escorcher.com #[eTrust.EScorcher]
127.0.0.1  www.eshopads2.com
127.0.0.1  estat.com
127.0.0.1  perso.estat.com #[Ewido.Spyware.Cookie.Estat]
127.0.0.1  prof.estat.com #[SecuritySpace.WebBug]
127.0.0.1  sky.estat.com
127.0.0.1  www.estat.com
127.0.0.1  gtb.etology.com
127.0.0.1  pages.etology.com
127.0.0.1  www.etracker.de
127.0.0.1  www.etxh.com #[Win32/Prosti.C]
127.0.0.1  ads.ero-advertising.com
127.0.0.1  adopt.euroclick.com #[Ewido.TrackingCookie.Euroclick]
127.0.0.1  cdn.euroclick.com
127.0.0.1  www.euroklik.nl #[EasyBar][HJTH.SinCity Dialer]
127.0.0.1  advert.eurotip.cz
127.0.0.1  www.euros4click.de
127.0.0.1  ad.eurosport.com #[oas.eurosport.com]
127.0.0.1  www.eurowebstats.com
127.0.0.1  www.everestpoker.com #[AdWare.Win32.Casino.t]
127.0.0.1  advert.exaccess.ru
127.0.0.1  dynamic.exaccess.ru
127.0.0.1  static.exaccess.ru
127.0.0.1  www.exchangead.com
127.0.0.1  exchange.bg
127.0.0.1  www.exchange.bg
127.0.0.1  exit-ad.de #[Ad-Aware.Tracking.Cookie]
127.0.0.1  exitexchange.com #[IE-SpyAd][SiteAdvisor.exitexchange.com]
127.0.0.1  ads.exitexchange.com
127.0.0.1  count.exitexchange.com #[McAfee.Cookie-Exitexchange]
127.0.0.1  images.exitexchange.com
127.0.0.1  www.exitexchange.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.exittrade.com
127.0.0.1  www.exittraffic.net #[SiteAdvisor.exittraffic.net]
127.0.0.1  syndication.exoclick.com
127.0.0.1  nyton.experclick.com #[p.mii.instacontent.net]
127.0.0.1  www.experclick.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads.expressindia.com
127.0.0.1  banners.expressindia.com
127.0.0.1  cdn.eyewonder.com #[SunBelt.EyeWonder]
127.0.0.1  pixel1097.everesttech.net
127.0.0.1  pixel1324.everesttech.net
127.0.0.1  pixel1370.everesttech.net
127.0.0.1  www.evidence-eliminator.com
127.0.0.1  evilman.cn #[Win32/TrojanDownloader.VB.APY]
127.0.0.1  ads2.exhedra.com
127.0.0.1  ads.expedia.com
127.0.0.1  www.eyeget.com #[McAfee.Adware-EyeGet]
127.0.0.1  feedback.eyereturn.com
127.0.0.1  resources.eyereturn.com
127.0.0.1  timespent.eyereturn.com
127.0.0.1  voken.eyereturn.com
127.0.0.1  ads.ezboard.com
127.0.0.1  eziin.com #[Adware.Eziin]
127.0.0.1  www.eziin.com
127.0.0.1  www.ezurl.co.kr #[Spyware.Ezurl]
# [F]
127.0.0.1  ads.facebook.com #[facebook-ads.vo.llnwd.net]
127.0.0.1  www.factorygames.com #[SiteAdvisor.factorygames.com]
127.0.0.1  banner.fairpoker.com #[AdWare.Win32.Casino.w]
127.0.0.1  tmp.farfly.org #[Trojan.Farfli]
127.0.0.1  www.fast-adv.it
127.0.0.1  www.fastfind.org #[TROJ_STARTPAG.KF][Win32/Adware.MediaBack]
127.0.0.1  fastonlineusers.com
127.0.0.1  fasttrack.nu
127.0.0.1  fastwebcounter.com
127.0.0.1  counter.fateback.com
127.0.0.1  counter1.fc2.com
127.0.0.1  www.ffxiforums.net #[Trojan-PSW.Win32.OnLineGames.kw]
127.0.0.1  alex.fileburst.com #[Win32/TrojanDropper.Agent.NBT]
127.0.0.1  adserver.filefront.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  findover.org #[Spamdexing]
127.0.0.1  search.findscout.com
127.0.0.1  www.findscout.com #[W32/Delf.KPZ]
127.0.0.1  ai.p.findology.com
127.0.0.1  banner.finn.no
127.0.0.1  ads.firingsquad.com
127.0.0.1  ads2.firingsquad.com
127.0.0.1  ads.firstgrand.com
127.0.0.1  firstwolf.org #[Downloader-BAC]
127.0.0.1  fishclix.com
127.0.0.1  www.fishclix.com
127.0.0.1  www.fish-screensaver.com #[AdWare.Win32.Gator.1008]
127.0.0.1  www.fjordbergen.com #[Win32/Spy.Banker.BIG]
127.0.0.1  www.fjjyjy.net #[Win32/Hipigon][W32.Fijjy]
127.0.0.1  cdn.flashedmail.com #[Parked?]
127.0.0.1  tracker1.flashedmail.com #[IE-SpyAd]
127.0.0.1  adserver4.fluent.ltd.uk
127.0.0.1  adserver.fmpub.net
127.0.0.1  dynamic.fmpub.net
127.0.0.1  static.fmpub.net
127.0.0.1  ads.fmwinc.com
127.0.0.1  www.foofle.net #[Backdoor.Foobot]
127.0.0.1  adcycle.footymad.net
127.0.0.1  www.forodeortodoncia.com #[Backdoor.IRC.Zapchast]
127.0.0.1  js.forrestersurveys.com
127.0.0.1  socratos.forrestersurveys.com
127.0.0.1  user.france.net.in #[Javascript.Exploit]
127.0.0.1  akcr.free.fr #[Win32/Spy.Bancos.U]
127.0.0.1  googlelite.free.fr #[Spamdexing]
127.0.0.1  ad.freecity.de
127.0.0.1  ads05.freecity.de
127.0.0.1  freecounters.xp.tl
127.0.0.1  maurobb.freecounter.it
127.0.0.1  www.freecounter.it
127.0.0.1  securinews.free.fr #[Trojan.Hexem]
127.0.0.1  www.freedownloadhq.com #[SiteAdvisor.freedownloadhq.com]
127.0.0.1  ad.freefind.com
127.0.0.1  www.freehitwebcounters.com
127.0.0.1  adverts.freeloader.com
127.0.0.1  freelogs.com
127.0.0.1  bar.freelogs.com
127.0.0.1  goo.freelogs.com
127.0.0.1  htm.freelogs.com
127.0.0.1  ico.freelogs.com
127.0.0.1  joe.freelogs.com
127.0.0.1  mom.freelogs.com
127.0.0.1  xyz.freelogs.com
127.0.0.1  adserver.freenet.de
127.0.0.1  freeonlineusers.com
127.0.0.1  www.free-ranking.de
127.0.0.1  www.freerip.com #[AdTool.Win32.MyWebSearch.ak]
127.0.0.1  freescanpro.com
127.0.0.1  www.freescanpro.com
127.0.0.1  free-stats.com
127.0.0.1  abbyssh.freestats.com
127.0.0.1  insurancejournal.freestats.com
127.0.0.1  www.freestat.ws
127.0.0.1  www.freestats.ws
127.0.0.1  banners.freett.com
127.0.0.1  count.freett.com
127.0.0.1  counters.freewebs.com
127.0.0.1  ads.freeonlinegames.com
127.0.0.1  stats.freeonlinegames.com
127.0.0.1  error.freewebsites.com
127.0.0.1  www.freewebsites.com
127.0.0.1  media.ftv-publicite.fr #[RealMedia]
127.0.0.1  fullddl.com
127.0.0.1  www.fullddl.com #[HTML/TrojanDownloader.XXXToolbar]
127.0.0.1  404.funpic.de
127.0.0.1  funppc.com
127.0.0.1  www.funppc.com
127.0.0.1  ads.futurenetworkusa.com
# [G]
127.0.0.1  ads.gad-network.com
127.0.0.1  adserver.gadu-gadu.pl
127.0.0.1  www.gamersbanner.com
127.0.0.1  ads.gameservers.com
127.0.0.1  ads.gamespy.com #[SpySweeper.Spy.Cookie]
127.0.0.1  adcontent.gamespy.com
127.0.0.1  ads.gamespyid.com
127.0.0.1  www.gameurdr.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  server.gamyun.net
127.0.0.1  www.gamyun.net #[Adware.GamyunIeToolbar]
127.0.0.1  ad.garantiarkadas.com
127.0.0.1  ads.gather.com
127.0.0.1  track.gawker.com #[WebBug]
127.0.0.1  js.gbeb.cc #[Javascript.Exploit]
127.0.0.1  haymarket-adserver.gcnpublishing.com
127.0.0.1  www.gebr-wachs.de #[Trojan.Mitglieder.C][Backdoor.Gaster]
127.0.0.1  sda.geek.com #[AdvertPro]
127.0.0.1  adserver.geenstijl.nl
127.0.0.1  kassa.geenstijl.nl
127.0.0.1  adserver.geizkragen.de
127.0.0.1  gd.geobytes.com #[obtains users location]
127.0.0.1  geotarget.info #[Whois.Blacklisted]
127.0.0.1  banners.geotarget.info
127.0.0.1  www.geotarget.info
127.0.0.1  www.geowhere.net #[SunBelt.GeoWhere Search]
127.0.0.1  get-access.host.sk #[McAfee.StartPage-IR]
127.0.0.1  getclicky.com
127.0.0.1  static.getclicky.com
127.0.0.1  www.getmusicvideocodes.com #[Malicious.Links.Zango]
127.0.0.1  www.getsmart.com
127.0.0.1  dlx.getupdate.com #[AdvWare.ToolBar.VB.b][Adware.Getup]
127.0.0.1  www.giantdating.com #[Spamdexing.adultfriendfinder]
127.0.0.1  banner.giantvegas.com
127.0.0.1  truehits.gits.net.th
127.0.0.1  truehits1.gits.net.th
127.0.0.1  ads.globo.com
127.0.0.1  ads.img.globo.com
127.0.0.1  glory-movy.net #[Javascript.Exploit]
127.0.0.1  duke.gocomics.com #[ads.uclick.com]
127.0.0.1  www.god74.com #[Trojan.Huanux]
127.0.0.1  www.godesktop.com #[SiteAdvisor.godesktop.com]
127.0.0.1  adserver2.goals365.com
127.0.0.1  www.go-and-search.com #[Spamdexing]
127.0.0.1  goglee.biz
127.0.0.1  www.goglee.biz
127.0.0.1  golden-keys.net #[Spamdexing]
127.0.0.1  banner.goldenpalace.com #[Tenebril.Tracking.Cookie]
127.0.0.1  stage.goldkey.com #[Parking Service]
127.0.0.1  goldstats.net
127.0.0.1  www.goldstats.net
127.0.0.1  www.goodhealth-search.com #[Spamdexing]
127.0.0.1  www.qooqlesearch.com #[Spamdexing]
127.0.0.1  www.goggle.com #[IE-SpyAd][typo squatter]
127.0.0.1  google-counter.com #[Win32/Spy.Banker.CKW]
127.0.0.1  www.google-counter.com #[Google.Warning]
127.0.0.1  google-moogle.com #[Spamdexing]
127.0.0.1  www.google-moogle.com
127.0.0.1  www.google-hard.com #[Win32/TrojanProxy.Agent.LK]
127.0.0.1  google-pharmacy.com #[Spamdexing]
127.0.0.1  goooglegulp.com #[Spamdexing]
127.0.0.1  www.gogogo.com #[PremiumTraffic.Parking Service]
127.0.0.1  partner.gonamic.de
127.0.0.1  www.goodsearchnow.com #[Trojan.Jakposh]
127.0.0.1  googlus.com #[Spamdexing]
127.0.0.1  adincl.gopher.com #[InfoSpace]
127.0.0.1  goserv.com #[VBS/Exploit.Phel.A]
127.0.0.1  stat.org.gosite.ws
127.0.0.1  gostats.com
127.0.0.1  as.gostats.com
127.0.0.1  c1.gostats.com
127.0.0.1  c2.gostats.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c3.gostats.com
127.0.0.1  c4.gostats.com #[Panda.Spyware:Cookie/GoStats]
127.0.0.1  ded.gostats.com
127.0.0.1  monster.gostats.com
127.0.0.1  webcounter.goweb.de
127.0.0.1  ads.goyk.com
127.0.0.1  www.gpt-pal.com #[Javascript.Exploit]
127.0.0.1  graffitifonts.com
127.0.0.1  www.graffitifonts.com #[Malicious.Links.Zango]
127.0.0.1  graficastrigo.com #[Trojan.Tabela.E]
127.0.0.1  www.gratis-toplist.de
127.0.0.1  adv.gratuito.st
127.0.0.1  dna-paterny-testing-in-1.com
127.0.0.1  greatfog.com #[Javascript.Exploit]
127.0.0.1  www.greasypalm.co.uk #[PcTools.GreasyPalm bar]
127.0.0.1  greencunt.org #[Javascript.Exploit]
127.0.0.1  grepblogs.net
127.0.0.1  grigcnt.info #[Javascript.Exploit]
127.0.0.1  adserver.gruprc.ro
127.0.0.1  publi.grupocorreo.es #[RealMedia]
127.0.0.1  ads.guru3d.com
127.0.0.1  www.g-wizzads.net #[adbureau.net]
# [H]
127.0.0.1  www.h148.cn #[Google.Warning]
127.0.0.1  ads2.haber3.com
127.0.0.1  www.handyarchive.com #[SiteAdvisor.handyarchive.com]
127.0.0.1  www.haosf128.com #[Google.Warning]
127.0.0.1  streamit.hardwarezone.com
127.0.0.1  ad1.hardware.no #[AdvertPro]
127.0.0.1  adserver.hardwareanalysis.com
127.0.0.1  www.harmonyhollow.net #[SiteAdvisor.harmonyhollow.net]
127.0.0.1  ads.harpers.org
127.0.0.1  hartim.com
127.0.0.1  ad0.haynet.com
127.0.0.1  ad.hbv.de
127.0.0.1  ads.heias.com
127.0.0.1  www.helpdesignonline.com #[server down?]
127.0.0.1  helpingfind.info #[SiteAdvisor.msiesettings.com]
127.0.0.1  www.henbang.net #[Adware.Henbang][SPYW_HAP.A]
127.0.0.1  www.hentaibanners.com
127.0.0.1  www.hentaicashmachine.com
127.0.0.1  www.hentaiclicks.com
127.0.0.1  www.hentaicounter.com
127.0.0.1  www.hentaihits.com
127.0.0.1  www.hentaipop.com #[Electronic Group Dialer]
127.0.0.1  www.hentaiseeker.com
127.0.0.1  www.hentaitoonami.com
127.0.0.1  ads.herbalsmokeshop.com
127.0.0.1  www.herbalsmokeshops.com
127.0.0.1  www2.hermoment.com
127.0.0.1  www.hermoment.com
127.0.0.1  ads.hexun.com
127.0.0.1  www.hey.lt
127.0.0.1  hiden.info #[Javascript.Exploit]
127.0.0.1  pubs.hiddennetwork.com
127.0.0.1  ads.highdefdigest.com
127.0.0.1  www.hiperstat.com
127.0.0.1  adserver.hispanoclick.com
127.0.0.1  www.hitscount.com
127.0.0.1  hits-counter.com
127.0.0.1  www.hits-counter.com
127.0.0.1  ctr.hitcounter-1.com
127.0.0.1  www.hit-counter-download.com
127.0.0.1  hithopper.com #[Adware.Hithopper]
127.0.0.1  www.hithopper.com #[ADW_HITHOPPER.A]
127.0.0.1  www.hitlogger.com #[server down?]
127.0.0.1  rdr.hitmngr.com
127.0.0.1  hitmodel.net
127.0.0.1  www.hit-counts.com
127.0.0.1  hit-now.com
127.0.0.1  www.hitscreamer.com
127.0.0.1  hitslog.com
127.0.0.1  h1.hitslog.com
127.0.0.1  s4.histats.com
127.0.0.1  s10.histats.com
127.0.0.1  s11.histats.com
127.0.0.1  www.hitstats.co.uk
127.0.0.1  hitstats.net
127.0.0.1  www.hittracking.com
127.0.0.1  images.hitwise.co.uk
127.0.0.1  anna.homeftp.net #[W32.Linkbot.A]
127.0.0.1  adserver.hostfinderguy.com
127.0.0.1  www.gontijoamaral.hpg.com.br #[Adware.Diginum]
127.0.0.1  www.adserver.home.pl
127.0.0.1  www.homeoffun.com #[SiteAdvisor.homeoffun.com]
127.0.0.1  counters.honesty.com
127.0.0.1  cgi.honesty.com #[MVPS.Criteria]
127.0.0.1  ad.hosting.pl
127.0.0.1  ns1.hosting101.biz #[JS/Small.DN]
127.0.0.1  hot8888.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  hot8888.cn #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  ad2.hotels.com
127.0.0.1  www.hot-lindsay.com #[Malicious.Links.Zango]
127.0.0.1  hotlinkbanners.com
127.0.0.1  www.hotlinkbanners.com
127.0.0.1  cgi.hotstat.nl
127.0.0.1  viewstat.hotstat.nl
127.0.0.1  hotstream.info
127.0.0.1  ad.howstuffworks.com #[RealMedia][SpySweeper.Spy.Cookie]
127.0.0.1  hpod.com
127.0.0.1  www.htmate2.com #[Cursor.MySpace]
127.0.0.1  adserver.html.it
127.0.0.1  click.html.it
127.0.0.1  vip.huigezi.com #[Backdoor.Graybird.Q][W32.Looked.F]
127.0.0.1  down.hunll.com #[BDS/Agent.ahj.701]
127.0.0.1  www.huxley-online.net #[Win32/Spy.Elite.10.A]
127.0.0.1  hyip-review.info #[Javascript.Exploit]
127.0.0.1  www.hypercounter.com
127.0.0.1  www.hypertracker.com #[SpySweeper.Spy.Cookie]
# [I]
127.0.0.1  ads.iafrica.com
127.0.0.1  ibm-ssl.com #[Trojan.DR.Cimuz.Gen.1]
127.0.0.1  www.i-clicks.net
127.0.0.1  hits.icdirect.com #[SunBelt.ICDirect.com]
127.0.0.1  hitctr01.icdirect.com
127.0.0.1  tracker.icerocket.com
127.0.0.1  ads.idgnow.com.br
127.0.0.1  banners.idg.com.br
127.0.0.1  adidm07.idmnet.pl
127.0.0.1  adidm.idmnet.pl
127.0.0.1  ie-exe.com #[AdWare.Win32.Softomate.x]
127.0.0.1  ad.ifrance.com
127.0.0.1  ijk.cc #[JS/Downloader-BCP]
127.0.0.1  image-catcher.com
127.0.0.1  bar.iebar8.com #[Adware.Navihelper]
127.0.0.1  stats.surfaid.ihost.com
127.0.0.1  adserver.ig.com.br
127.0.0.1  gate.ilogbox.com
127.0.0.1  ads.imeem.com
127.0.0.1  bbn.img.com.ua
127.0.0.1  content-ads.impactengine.com
127.0.0.1  www.impregnable.net #[TrojanDownloader.Win32.VB.dw][Trojan.Win32.StartPage.kk]
127.0.0.1  ads.ims.nl
127.0.0.1  in2search.org #[JS/TrojanDropper.Tivso.gen]
127.0.0.1  dns.in2search.org
127.0.0.1  s201.indexstats.com
127.0.0.1  stats.indexstats.com #[Analytics Tracking Code]
127.0.0.1  stats.indextools.com #[eTrust.Tracking.Cookie]
127.0.0.1  campaign.indieclick.com
127.0.0.1  optimize.indieclick.com
127.0.0.1  adcenter.in2.com
127.0.0.1  get.inetbar.com #[SunBelt.INetBar]
127.0.0.1  juggler.inetinteractive.com
127.0.0.1  rotator.juggler.inetinteractive.com
127.0.0.1  banners.inetfast.com
127.0.0.1  adserving.infinite-ads.com
127.0.0.1  www.infineo.de #[Win32/Spy.Banker.AWA]
127.0.0.1  www.info--bits.com
127.0.0.1  infospot.infocious.com
127.0.0.1  ads.infospace.com #[ADW_DEALHELPER.C]
127.0.0.1  msxml.infospace.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.infotelsrl.com #[eTrust.Infotel srl]
127.0.0.1  ads.injersey.com #[RealMedia]
127.0.0.1  bimonline.insites.be
127.0.0.1  ads.intellicast.com #[weather.com]
127.0.0.1  strtt.interfree.it #[W32.Iberio]
127.0.0.1  counter.internet.ge
127.0.0.1  indiads.com
127.0.0.1  images.indiads.com
127.0.0.1  servedby.indiads.com #[RealMedia]
127.0.0.1  popups.infostart.com #[eTrust.Popups.infostart.com]
127.0.0.1  www.imiclk.com
127.0.0.1  inexplorer.com
127.0.0.1  toolbar.inexplorer.com #[Win32/Parite.B]
127.0.0.1  www.inexplorer.com
127.0.0.1  www.inpopo.com #[W32.Validin]
127.0.0.1  oc.inspectorclick.com
127.0.0.1  trax.inspectorclick.com
127.0.0.1  v2.inspectorclick.com
127.0.0.1  v3.inspectorclick.com
127.0.0.1  instantbuzz.com #[NOD32.Win32/Adware.InstantBuzz]
127.0.0.1  www2.instantbuzz.com
127.0.0.1  www.instantbuzz.com #[Adware.ToolBar.InstantBuzz.a]
127.0.0.1  media.intelia.it
127.0.0.1  anm.intelli-direct.com #[IntelliTracker]
127.0.0.1  info.intelli-direct.com
127.0.0.1  oxfam.intelli-direct.com
127.0.0.1  tui.intelli-direct.com
127.0.0.1  www.intelli-tracker.com
127.0.0.1  intraviewer.net #[server down?]
127.0.0.1  www.intraviewer.net
127.0.0.1  newadserver.interfree.it #[Adcycle]
127.0.0.1  internet-explorer.name #[Trojan-Clicker.Win32.Agent.ip]
127.0.0.1  www.internet-explorer.name
127.0.0.1  www.interstats.nl
127.0.0.1  www.intrastats.com
127.0.0.1  channels.intwined.com #[Adware/ToolBar.ISearch.c]
127.0.0.1  search.intwined.com
127.0.0.1  www.intwined.com #[McAfee.Adware-SSF!Hosts]
127.0.0.1  www.invinc.com #[Troj/Dloader-J]
127.0.0.1  www.ipcounter.de
127.0.0.1  ad2.ip.ro
127.0.0.1  ads.ipowerweb.com
127.0.0.1  www.ipqwe.com #[Exploit.ANI]
127.0.0.1  content.ipro.com #[WebBug]
127.0.0.1  www.ipstat.com
127.0.0.1  adzones.ircspy.com
127.0.0.1  isecurepages.net #[Google.Warning]
127.0.0.1  www.isecurepages.net #[IFrame.Exploit]
127.0.0.1  www.istats.nl
127.0.0.1  a.isohunt.com
127.0.0.1  adserver1.isohunt.com
127.0.0.1  ads.isoftmarketing.com
127.0.0.1  banman.isoftmarketing.com
127.0.0.1  ads1.itadnetwork.co.uk
127.0.0.1  itcompany.com #[SunBelt.Family Cyber Alert]
127.0.0.1  www.itcompany.com #[Symantec.Spyware.CyberAlert]
127.0.0.1  itisbest.info #[Spamdexing]
127.0.0.1  itnos.info
127.0.0.1  www.itrackpages.com
127.0.0.1  ilead.itrack.it
127.0.0.1  adserver.itsfogo.com
127.0.0.1  partnerfeed.itsfogo.com
127.0.0.1  www1.itsun.com
127.0.0.1  www8.itsun.com
127.0.0.1  ads.itv.com #[adbureau.net]
127.0.0.1  barafranca.iwarp.com #[Win32/Spy.ProAgent]
127.0.0.1  www.iwebmusic.com
127.0.0.1  iwebtunes.com #[FTC Action]
127.0.0.1  www.iwebtunes.com
# [J]
127.0.0.1  ad.jamba.de
127.0.0.1  ad.jamba.net
127.0.0.1  ad.jamster.com
127.0.0.1  www.jcount.com
127.0.0.1  www.jellycounter.com
127.0.0.1  www.jethit.com
127.0.0.1  t1.jfglass.net #[Trojan.Booha]
127.0.0.1  dl.jiangmin.com #[Adware-BDSearch.dr]
127.0.0.1  jimmybuttons.com #[eTrust.Win32/Nirbot]
127.0.0.1  www.jm-my.com #[BackDoor-CXI]
127.0.0.1  ad.joetec.net
127.0.0.1  jointmediagroup.com #[Trojan-Spy.Win32.Delf.uc]
127.0.0.1  ads.jokaroo.com
127.0.0.1  jpedownload.joltid.com
127.0.0.1  banners.joost.com
127.0.0.1  ads.jossip.com
127.0.0.1  pastorale.jpn.org #[Win32/Spy.Banker.AHY]
127.0.0.1  www.joltid.com #[Adware.P2PNetworking][SPYW_PPNETWORK.B]
127.0.0.1  promotion.jpds.com
127.0.0.1  www.jprmthome.com #[Trojan-PSW.Win32.Maran.ei]
127.0.0.1  www.jstracker.com
127.0.0.1  ads.jt.org
127.0.0.1  www.justfreegames.com #[AdWare.Win32.Relevant.a]
127.0.0.1  925.vip.jx828.net #[HTML/Exploit.IframeBof]
127.0.0.1  jxdoe.com #[Win32/TrojanDownloader.Ani.Gen]
# [K]
127.0.0.1  www.k265.com #[Adware.Borlan]
127.0.0.1  stat.katalysatormedia.no
127.0.0.1  kazantip-top.com
127.0.0.1  www.kazantip-top.com #[HTML/Exploit.VMLFill]
127.0.0.1  ads.webfever.kadserver.com
127.0.0.1  ads.deblok.net.kadserver.com
127.0.0.1  ads.zebest-3000.net.kadserver.com
127.0.0.1  countus.get.kadserver.com
127.0.0.1  geo113prod.kadserver.com
127.0.0.1  get.kadserver.com
127.0.0.1  scripts.kataweb.it
127.0.0.1  kazaalite.pl
127.0.0.1  www.kazaalite.pl #[MHTMLRedir.Exploit]
127.0.0.1  gavzad.keenspot.com
127.0.0.1  ad.kewlbox.com
127.0.0.1  a.keyrun.com #[Adware-TargetAD]
127.0.0.1  u.keyrun.com
127.0.0.1  union.keyrun.com
127.0.0.1  ww.keyrun.com
127.0.0.1  www1.keyrun.com
127.0.0.1  www.keyrun.com
127.0.0.1  banner.kiev.ua
127.0.0.1  kikclick.com #[Spamdexing]
127.0.0.1  adserve.kikizo.com
127.0.0.1  union.db.kingsoft.com #[PopupAds]
127.0.0.1  www.kiss-search.net
127.0.0.1  www.kisssearch.com #[Umax]
127.0.0.1  ebay.kisswin.com #[Adware.Kiswin]
127.0.0.1  kjsc.org #[Win32/Spy.Banker.ANV]
127.0.0.1  ads.kleinman.com #[Adcycle]
127.0.0.1  www.klikvipresources.com #[Spamdexing]
127.0.0.1  gfx.klipmart.com #[gfx.dvlabs.com]
127.0.0.1  kt3.kliptracker.com
127.0.0.1  kt4.kliptracker.com
127.0.0.1  www.kliptracker.com
127.0.0.1  ads.klixxx.com
127.0.0.1  www.km-nyc.com #[W32.Lecna.A]
127.0.0.1  click.kmindex.ru
127.0.0.1  counter.kmindex.ru
127.0.0.1  counting.kmindex.ru
127.0.0.1  www.kmindex.ru
127.0.0.1  www.knacads.com
127.0.0.1  xx.ko51.com #[Google.Warning]
127.0.0.1  images.kolmic.com
127.0.0.1  pics.kolmic.com #[Parking Service]
127.0.0.1  ads.komli.com
127.0.0.1  www.kompass-intl.com #[Win32/Adware.Toolbar.PowerSearch]
127.0.0.1  de.komtrack.com
127.0.0.1  koolbar.net #[Adware Bundler][ADW_KOOLBAR.A]
127.0.0.1  www.koolbar.net #[eTrust.AutoSearch]
127.0.0.1  sitestat.kpn-is.nl
127.0.0.1  kuaiso.com #[AdWare.Win32.Kuaiso.a]
127.0.0.1  toolsbar.kuaiso.com #[Adware.Kuaiso]
127.0.0.1  www.kuaiso.com
127.0.0.1  kustusch.com #[Javascript.Exploit]
127.0.0.1  www.kz163.net #[Win32/Virut]
# [L]
127.0.0.1  alwaysforfriend.land.ru #[Trojan-Downloader.Win32.Banload.bdp]
127.0.0.1  www.animacoes.land.ru #[Downloader.Swif.B]
127.0.0.1  landinghall.com #[Spamdexing]
127.0.0.1  www.latinbusca.com #[Adware-CommanderNET]
127.0.0.1  ads.lawnsite.com
127.0.0.1  layer-ads.de
127.0.0.1  www.layer-ads.de
127.0.0.1  banner.lbs.km.ru
127.0.0.1  iframe.leadacceptor.com
127.0.0.1  leakedcelebvideos.com #[Win32/TrojanDownloader.Agent.BCZ]
127.0.0.1  www.leakedcelebvideos.com
127.0.0.1  lem0n.info #[server down?]
127.0.0.1  pubs.lemonde.fr
127.0.0.1  www.leopardsearch.com
127.0.0.1  www.letusearch.com #[Google.Warning]
127.0.0.1  ts1.lexmark.com
127.0.0.1  leythosthestalker.com
127.0.0.1  www.leythosthestalker.com
127.0.0.1  adserver.libero.it
127.0.0.1  adv-banner.libero.it
127.0.0.1  phpads.lime.com
127.0.0.1  link.ru
127.0.0.1  link.link.ru
127.0.0.1  www.linkads.net
127.0.0.1  ads.linki.nl
127.0.0.1  www.linkads.de
127.0.0.1  linkbuddies.com
127.0.0.1  banners.linkbuddies.com
127.0.0.1  www.linkbuddies.com
127.0.0.1  www.linkcounter.com
127.0.0.1  linksexchange.net
127.0.0.1  linkexchange.ru
127.0.0.1  web.linkexchange.ru
127.0.0.1  www.linkexchange.ru
127.0.0.1  link4link.com
127.0.0.1  plus.link4link.com
127.0.0.1  www.links4trade.com
127.0.0.1  escati.linkopp.net
127.0.0.1  www.linkopp.net
127.0.0.1  click.linkstattrack.com #[SiteAdvisor.linkstattrack.com]
127.0.0.1  www.linkpal.biz #[Trojan.Win32.LowZones.dr][server down?]
127.0.0.1  linktarget.com
127.0.0.1  banner.linktech.cn
127.0.0.1  www.linkworth.com
127.0.0.1  ads.linuxjournal.com
127.0.0.1  www.ligue13.com #[Win32/Spy.Banker.BIG]
127.0.0.1  www.liveads.org
127.0.0.1  livecounter.net
127.0.0.1  www.livecounter.net
127.0.0.1  image.adv.livedoor.com
127.0.0.1  js.livehelper.com
127.0.0.1  newbrowse.livehelper.com
127.0.0.1  ads.livescore.com
127.0.0.1  traffic.liveuniversenetwork.com
127.0.0.1  traffic.livevideo.com
127.0.0.1  broadent.vo.llnwd.net
127.0.0.1  lw.lnkworld.com
127.0.0.1  loadz.biz #[Javascript.Exploit]
127.0.0.1  omnituretrack.local.com
127.0.0.1  ads.locators.com
127.0.0.1  toolbar.locators.com #[AdWare.Win32.Locator.f]
127.0.0.1  www.lojastal.com.br #[Win32/Spy.Banker.ANV]
127.0.0.1  lol.to #[HTML/Exploit.Mht]
127.0.0.1  err.lolipop.jp
127.0.0.1  www.lookde5.com #[W32.Looked]
127.0.0.1  lookoutsoft.net #[SiteAdvisor.lookoutsoft.net]
127.0.0.1  screensavers.lookoutsoft.net
127.0.0.1  a.loomia.com #[Tracking.Cookie]
127.0.0.1  www.lookoutsoft.net #[AdWare.Win32.WinAD.b]
127.0.0.1  www.lords-of-havoc.de #[Trojan.Mitglieder.C][Backdoor.Gaster]
127.0.0.1  lolteens.in #[Haxdoor.Exploit]
127.0.0.1  lottery-news.info #[HTML/TrojanDownloader.Agent.NAB]
127.0.0.1  hexusads.fluent.ltd.uk
127.0.0.1  www.luxemil.com #[Google.Warning]
127.0.0.1  ads-apsa.lvz-online.de
127.0.0.1  www.lynxtrack.com
127.0.0.1  counter.lyricsdownload.com
# [M]
127.0.0.1  m2k.ru
127.0.0.1  ad.m5prod.net
127.0.0.1  ad.m-adx.com
127.0.0.1  media.m-adx.com
127.0.0.1  www.macrcmedia.com #[Exploit.ANI]
127.0.0.1  www.macrcmedia.net
127.0.0.1  ads.madisonavenue.com
127.0.0.1  resource.madisonavenue.com
127.0.0.1  textads.madisonavenue.com
127.0.0.1  www.madrascements.com #[Win32/Spy.Banker.Big]
127.0.0.1  banner.magicboxcasino.com #[AdWare.Win32.Casino.w]
127.0.0.1  msn-sexoweb.mail15.com #[Win32/Spy.Banker.ANV]
127.0.0.1  humortadela.mail15.com #[Win32/Spy.Banker.ANV]
127.0.0.1  www.novogerador.mail15.com
127.0.0.1  www.uolcard.mail15.com #[Trojan-Spy.Win32.Banker.ark]
127.0.0.1  voegol.mail15.com #[Win32/Spy.Banker.ANV]
127.0.0.1  humortadela0.mail333.com #[Win32/Spy.Banker.AHY]
127.0.0.1  destino-gol.mail333.com #[Win32/Spy.Banker.BCK]
127.0.0.1  www.messengerbeta.mail333.com #[Win32/Spy.Banker.BCK]
127.0.0.1  mair.net #[Realtracker]
127.0.0.1  ads.marketing-internet.com
127.0.0.1  marketing-know-how.com #[TR/Dldr.iBill.V]
127.0.0.1  adsnew.maktoob.com #[AdvertPro]
127.0.0.1  aw.masterstats.com
127.0.0.1  erotic.masterstats.com
127.0.0.1  image.masterstats.com
127.0.0.1  link.masterstats.com
127.0.0.1  vw.masterstats.com #[Ewido.TrackingCookie.Masterstats]
127.0.0.1  adserver.matchcraft.com
127.0.0.1  www.maxi-music.fr #[Win32/Spy.Banker.ANV]
127.0.0.1  ads.maxivip.fr
127.0.0.1  sitestat.mayoclinic.com
127.0.0.1  ads.mcafee.com
127.0.0.1  directads.mcafee.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www2.md80.cn
127.0.0.1  www.md80.cn #[W32.Validin]
127.0.0.1  tracker.measuremap.com
127.0.0.1  mcmads.mediacapital.pt #[DoubleClick]
127.0.0.1  matrix.mediavantage.de
127.0.0.1  adland.medialand.ru
127.0.0.1  adnet.medialand.ru
127.0.0.1  content.medialand.ru
127.0.0.1  ads.mediamayhemcorp.com
127.0.0.1  ads.mediaodyssey.com
127.0.0.1  acvs.mediaonenetwork.net
127.0.0.1  acvsrv.mediaonenetwork.net
127.0.0.1  ads1.mediaops.com.br
127.0.0.1  ad2.pl.mediainter.net
127.0.0.1  servedby.mediaplace.tv #[ad.firstadsolution.com]
127.0.0.1  media-servers.net
127.0.0.1  search.mediatarget.com
127.0.0.1  ads.mediaturf.net #[McAfee.Cookie-Mediaturf]
127.0.0.1  adv.medscape.com #[ads.webmd.com]
127.0.0.1  megabablo.info
127.0.0.1  www.megastats.com
127.0.0.1  exit.megago.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.megago.com #[typo squatter]
127.0.0.1  www.mercuras.com
127.0.0.1  reklama.metacafe.com
127.0.0.1  adserv2.meritdesigns.com
127.0.0.1  ads.metropol.dk
127.0.0.1  automagazine.metriweb.be
127.0.0.1  hln-frinfos.metriweb.be
127.0.0.1  levif.metriweb.be
127.0.0.1  line01.metriweb.be #[Ad-Aware.Tracking.Cookie]
127.0.0.1  line02.metriweb.be
127.0.0.1  line03.metriweb.be
127.0.0.1  line04.metriweb.be #[SpySweeper.Spy Cookie]
127.0.0.1  line05.metriweb.be
127.0.0.1  line06.metriweb.be
127.0.0.1  line07.metriweb.be #[Panda.Spyware:Cookie]
127.0.0.1  line08.metriweb.be
127.0.0.1  line09.metriweb.be
127.0.0.1  line10.metriweb.be
127.0.0.1  line11.metriweb.be
127.0.0.1  line12.metriweb.be
127.0.0.1  line13.metriweb.be
127.0.0.1  line14.metriweb.be
127.0.0.1  line15.metriweb.be
127.0.0.1  line16.metriweb.be
127.0.0.1  line17.metriweb.be
127.0.0.1  line18.metriweb.be
127.0.0.1  line19.metriweb.be
127.0.0.1  line20.metriweb.be
127.0.0.1  line24.metriweb.be
127.0.0.1  line26.metriweb.be
127.0.0.1  line32.metriweb.be
127.0.0.1  rtbf09.metriweb.be
127.0.0.1  skynet-news.metriweb.be
127.0.0.1  zattevrienden.metriweb.be
127.0.0.1  m-gallery.org #[Javascript.Exploit]
127.0.0.1  pubs.mgn.net #[Grolier Network]
127.0.0.1  www.mgshareware.com #[AdTool.Win32.MyWebSearch.ak]
127.0.0.1  microsoftout.com #[Phish.site]
127.0.0.1  ads.milenio.com
127.0.0.1  www.milesdebanners.com
127.0.0.1  adc1.mingpao.com
127.0.0.1  ads.mininova.org
127.0.0.1  www.mini-player.com #[5MOF Mini-Player]
127.0.0.1  counter.mirohost.net
127.0.0.1  miron555.org #[Javascript.Exploit]
127.0.0.1  misofthelp.com
127.0.0.1  www.misofthelp.com #[Google Warning]
127.0.0.1  banner.missbingo.com #[AdWare.Win32.Casino.ae]
127.0.0.1  banner.missingkids.com
127.0.0.1  misterbanner.com
127.0.0.1  ads.mixi.jp
127.0.0.1  img.ads.mixi.jp
127.0.0.1  www.mlclick.com
127.0.0.1  vod.mmdy.org #[McAfee.StartPage-JN!CC32C55]
127.0.0.1  www.mmoi.cn #[Javascript.Exploit]
127.0.0.1  timeout.mmy88.cn #[Google.Warning]
127.0.0.1  www.mnogotrafa.net #[Spamdexing]
127.0.0.1  banners.mobilesidewalk.com
127.0.0.1  ads.mobygames.com
127.0.0.1  smile.modchipstore.com
127.0.0.1  survey2.modernmindsoftware.com
127.0.0.1  banners.mojoflix.com
127.0.0.1  ad.mokead.com #[Trojan.Daekom]
127.0.0.1  w5.mokead.com
127.0.0.1  www.mokead.com #[W32/DLoader.VZN]
127.0.0.1  ads.monster.com
127.0.0.1  adserver.monster.com #[SunBelt.AdServer.Monster.com]
127.0.0.1  adserver.a.in.monster.com
127.0.0.1  ads.monstermoving.com
127.0.0.1  cookie.monster.com #[SunBelt.cookie.monster]
127.0.0.1  www.moratoriumx.net #[JS/TrojanDownloader.Agent.BI]
127.0.0.1  m1.webstats.motigo.com
127.0.0.1  www.motioncodecs.com #[Win32/TrojanDownloader.Mediket]
127.0.0.1  www.movies.net.cn #[AdWare.Win32.AdBlaster.b]
127.0.0.1  www.mp3downloadhq.com #[SiteAdvisor.mp3downloadhq.com]
127.0.0.1  mp3today.net
127.0.0.1  mpamexit.com
127.0.0.1  msedulearner.com #[server down?]
127.0.0.1  adfarm.mserve.ca
127.0.0.1  www.messagetag.com #[Email tracker]
127.0.0.1  msgtag.com
127.0.0.1  img.msgtag.com
127.0.0.1  www.msgtag.com
127.0.0.1  redirect.msupdate.net #[AdWare.Win32.SaveNow.bj]
127.0.0.1  mswindowsupdate.info
127.0.0.1  www.mswindowsupdate.info
127.0.0.1  h.mt12.net #[Win32/PSW.Lineage.AEL][W32/HLLP.Philis.ar]
127.0.0.1  multi1.rmuk.co.uk #[RealMedia]
127.0.0.1  www.muangboranjournal.com #[Win32/Spy.Banker.AHY]
127.0.0.1  www.multiclinmed.com.br #[Win32/PSW.Legendmir.ATE]
127.0.0.1  mussicalcardss.smtp.ru #[Win32/Spy.Banker.AHY]
127.0.0.1  www.musicmass.com #[HJTH.C2Media/LOP variant]
127.0.0.1  www.mumy8.com #[Exploit.ANI]
127.0.0.1  mvr.us #[Parasite.NavExcel][server down?]
127.0.0.1  www.mvr.us
127.0.0.1  click.myad.cn
127.0.0.1  click2.myad.cn
127.0.0.1  img.myad.cn
127.0.0.1  new.myad.cn
127.0.0.1  www.myadtrack.com #[Email Tracker]
127.0.0.1  ads.mybale.com
127.0.0.1  ipub.mybloglog.com
127.0.0.1  pub.mybloglog.com
127.0.0.1  track.mybloglog.com #[Yahoo Tracking Service]
127.0.0.1  track2.mybloglog.com
127.0.0.1  track3.mybloglog.com
127.0.0.1  mycashbank.co.kr
127.0.0.1  key.mycashbank.co.kr #[Trojan.Daum]
127.0.0.1  get.mycounter.com.ua
127.0.0.1  www.mycreditoweb.com
127.0.0.1  mydns-ns.info #[Win32/Spy.Banker.CKW]
127.0.0.1  www.myemessenger.com
127.0.0.1  www.myfriendspy.com
127.0.0.1  liveupdate.myim.cn #[Adware.BeSys]
127.0.0.1  www.mylinker.net #[Adware.MyLinker]
127.0.0.1  www.mylottoadserv.com
127.0.0.1  rm.myoc.com
127.0.0.1  wintercat.diy.myrice.com #[Win32/TrojanDownloader.Tiny.Y]
127.0.0.1  my-securedoc.com #[Downloader.Goobiz]
127.0.0.1  www.my-securedoc.com
127.0.0.1  mysessoblog.com
127.0.0.1  www.mysessoblog.com #[Downloader.Goobiz]
127.0.0.1  www.myspacebar.com #[SunBelt.Scam.MySpaceBar]
127.0.0.1  www.myspacetracer.com
127.0.0.1  myspacev.net #[MySpace.Exploit]
127.0.0.1  mystabcounter.info #[Google Warning]
127.0.0.1  stat.mystat.hu
127.0.0.1  www.mystats.nl
127.0.0.1  www2.mystats.nl
127.0.0.1  c.mystat-in.net
127.0.0.1  f2.n1.b.mystat-in.net
127.0.0.1  ___id___.c.mystat-in.net
127.0.0.1  061606084448.c.mystat-in.net
127.0.0.1  070806142521.c.mystat-in.net
127.0.0.1  102106151057.c.mystat-in.net
127.0.0.1  112006133326.c.mystat-in.net
# [N]
127.0.0.1  hit.namimedia.com
127.0.0.1  ads.nandomedia.com #[McAfee.Cookie-Nandomedia]
127.0.0.1  adserver.nav2.net
127.0.0.1  adcreative.naver.com
127.0.0.1  nv1.ad.naver.com
127.0.0.1  c1.navrcholu.cz
127.0.0.1  popsearch.nbcsearch.com
127.0.0.1  xml.nbcsearch.com
127.0.0.1  www.nbcsearch.com #[exactsearch.net]
127.0.0.1  sd.ncast.cn #[Adware.NCast]
127.0.0.1  www.ncph.net #[Exploit.ANI]
127.0.0.1  img1.ncsreporting.com
127.0.0.1  www.ncsreporting.com
127.0.0.1  ndparking.com #[Parking Service]
127.0.0.1  www.ndparking.com
127.0.0.1  www.neima.net #[Win32/Spy.Banker.AHY]
127.0.0.1  ads.neogen.bg
127.0.0.1  ads.neogen.ro
127.0.0.1  monitor.neogen.ro
127.0.0.1  ads.neowin.net
127.0.0.1  neocounter.neoworx-blog-tools.net
127.0.0.1  banman.nepsecure.co.uk #[Ban Man Pro Banner Code]
127.0.0.1  banners.netcraft.com
127.0.0.1  www.netdirect.nl
127.0.0.1  beta-hints.netflame.cc
127.0.0.1  hints.netflame.cc #[Fireclick Web Analytics]
127.0.0.1  ssl-hints.netflame.cc
127.0.0.1  trizvez.netfirms.com #[Win32/Spy.Banker]
127.0.0.1  ad.netgoo.com
127.0.0.1  adv.netinfo.bg
127.0.0.1  tracker.netklix.com
127.0.0.1  stat.netlogic.ru #[NetLogic Logger]
127.0.0.1  webstats.netlogics.nl
127.0.0.1  www.netmaxx.com
127.0.0.1  counter.netmore.net
127.0.0.1  ads.netrition.com
127.0.0.1  servedby.netshelter.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.network-tool.net #[Trojan.Magise]
127.0.0.1  www.new-phpmailer.com #[Win32/Bifrose.E]
127.0.0.1  i.nuseek.com #[Parking Service]
127.0.0.1  www1.nuseek.com
127.0.0.1  www2.nuseek.com #[overture.com]
127.0.0.1  www3.nuseek.com
127.0.0.1  ads.newdream.net
127.0.0.1  ads.newgrounds.com
127.0.0.1  ads.newsint.co.uk
127.0.0.1  www.newweb.com.cn #[Adware.NewWeb]
127.0.0.1  ads1.nexdra.com
127.0.0.1  adq.nextag.com #[McAfee.Cookie-Nextag]
127.0.0.1  nextgenstats.com
127.0.0.1  www.nextgenstats.com
127.0.0.1  www.ngp-mac.com #[Win32/Spy.Banker.AHY]
127.0.0.1  www.nice8.org #[W32.Drom]
127.0.0.1  nickatt.info #[Google.Warning][server down?]
127.0.0.1  www.nipr.ws #[Trojan.Chuvazada]
127.0.0.1  www.nlbanner.nl
127.0.0.1  ads.nordichardware.com
127.0.0.1  ads.nordichardware.se
127.0.0.1  www.nordicgold.com #[Win32/Spy.Banker.AHY]
127.0.0.1  www.norton-nod32.com #[Trojan.Win32.Pakes]
127.0.0.1  www.nortonproject.com #[AdWare.Win32.Softomate.j][Adware/ToolBar.ISearch.c]
127.0.0.1  ad.nozonedata.com #[Ad-Aware Tracking.Cookie]
127.0.0.1  ad1.nozonedata.com
127.0.0.1  ad.nrk.no
127.0.0.1  nsismedia.net #[SunBelt.NSIS Media]
127.0.0.1  www.nsismedia.net
127.0.0.1  ns2.iad1.nssrv.com
127.0.0.1  ntlligent.info #[Spamdexing]
127.0.0.1  ad.nttnavi.co.jp
127.0.0.1  banner.nttnavi.co.jp
127.0.0.1  cdn.nvero.net
127.0.0.1  e.nvero.net
127.0.0.1  ads.nyi.net
127.0.0.1  nzads.net.nz
# [O]
127.0.0.1  adserver.o2.pl
127.0.0.1  banner.oddcast.com
127.0.0.1  banner-a.oddcast.com
127.0.0.1  banner-d.oddcast.com
127.0.0.1  oemtop.com #[Google Warning]
127.0.0.1  www.oemtop.com
127.0.0.1  www.ok8vs.com #[Exploit.ANI]
127.0.0.1  www.okvs8.com #[Exploit.ANI]
127.0.0.1  okcounter.com #[IE-SpyAd][eTrust.Tracking.Cookie]
127.0.0.1  www.okww.net #[Trojan.StartPage.C]
127.0.0.1  ads.oneplace.com
127.0.0.1  stat.onestat.com #[Panda.Spyware:Cookie/onestat.com][Ad-Aware.Tracking.Cookie]
127.0.0.1  www.onestat.com #[Ewido.TrackingCookie.Onestat]
127.0.0.1  www.onestatfree.com
127.0.0.1  one.ru
127.0.0.1  cnt.one.ru
127.0.0.1  stats0.one.ru
127.0.0.1  stats1.one.ru
127.0.0.1  stats2.one.ru
127.0.0.1  ads.onemodelplace.com
127.0.0.1  reklama.onet.pl
127.0.0.1  onlinecount.com
127.0.0.1  online-service.cc
127.0.0.1  www.online-service.cc #[Trojan.Magise]
127.0.0.1  adserver.online-tech.com
127.0.0.1  lifemediahouse1.onlinewelten.com
127.0.0.1  onlyfreebies.net #[Spamdexing]
127.0.0.1  www.onlyscreensavers.com #[SiteAdvisor.onlyscreensavers.com]
127.0.0.1  www.openadnetwork.com
127.0.0.1  s17.opentracker.net
127.0.0.1  s27.opentracker.net
127.0.0.1  server1.opentracker.net
127.0.0.1  server10.opentracker.net
127.0.0.1  invitation.opinionbar.com
127.0.0.1  ccc00.opinionlab.com
127.0.0.1  ccc01.opinionlab.com #[msn.com]
127.0.0.1  rate.opinionlab.com
127.0.0.1  www.opinionlab.com
127.0.0.1  by.optimost.com
127.0.0.1  optlynx.com #[Adware.Optserve]
127.0.0.1  optmedia.jp
127.0.0.1  ad.orbitel.bg
127.0.0.1  ads.orsm.net
127.0.0.1  otx5.otxresearch.com
127.0.0.1  otx.ifilm.com #[OTXMedia.dll]
127.0.0.1  survey.otxresearch.com #[TrojanDownloader.OTXloader.A][MVPS.Criteria]
127.0.0.1  www.otxresearch.com #[Sophos.OTXLoader][Trojan.OTXLoader]
127.0.0.1  our-counter.biz #[ISANS.Alert]
127.0.0.1  liveupdate.ourxin.com #[Adware.AllSum]
127.0.0.1  www.ourxin.com #[Dr.Web.Adware.CFS][Trojan.Cfs]
127.0.0.1  adpopper.outblaze.com #[ADW_BBINSTALL.B][bargain-buddy.net]
127.0.0.1  adp4.us4.outblaze.com
127.0.0.1  adserver.hk.outblaze.com
127.0.0.1  adserver.us.outblaze.com
127.0.0.1  download2.us4.outblaze.com #[HJTH.Bargain Buddy]
127.0.0.1  www.overpeer.com #[Trojan.Wimad]
127.0.0.1  pub.oxado.com
127.0.0.1  oya.ru #[Javascript.Exploit][server down?]
# [P]
127.0.0.1  www.p5ip.com #[Exploit.ANI]
127.0.0.1  ad1.pamedia.com.au
127.0.0.1  ad2.pamedia.com.au
127.0.0.1  www.pantanalvip.com.br #[McAfee.Downloader-AFV]
127.0.0.1  park.parkingpanel.com
127.0.0.1  counter.paradise.net.nz
127.0.0.1  parladent-doc.org #[Backdoor.Haxdoor.L]
127.0.0.1  ads.partnerlogic.net
127.0.0.1  static.partnerlogic.net
127.0.0.1  update.passivecow.com #[Trojan.Win32.VB.aft][Adware.Superlogy]
127.0.0.1  traf.paycash.cc #[IFrame.Exploit]
127.0.0.1  b1.perfb.com
127.0.0.1  metrics.performancing.com
127.0.0.1  pmetrics.performancing.com
127.0.0.1  www.pcbutts1.com #[Unauthorized Downloads][SiteAdvisor.pcbutts1.com]
127.0.0.1  www.pc-localhost.com #[Win32/TrojanClicker.Agent.NBY]
127.0.0.1  ads.pcper.com
127.0.0.1  www.pc-test.net
127.0.0.1  ads.pcworld.com.br
127.0.0.1  pediki.biz #[Spamdexing]
127.0.0.1  ad1.peel.com
127.0.0.1  ad3.peel.com #[SunBelt.Peel]
127.0.0.1  ads.peel.com
127.0.0.1  ad4.peel.com #[Tenebril.Tracking.Cookie]
127.0.0.1  ads5.peel.com
127.0.0.1  freeps3.peel.com
127.0.0.1  www.peel.com
127.0.0.1  www.peel.net
127.0.0.1  ads.pennyweb.com #[addynamix.com]
127.0.0.1  banners.pennyweb.com
127.0.0.1  errors.perfectgonzo.com
127.0.0.1  pluginx.perfectgonzo.com
127.0.0.1  ads.periodistadigital.com
127.0.0.1  www.peruvianmarket.com #[Trojan.Beagooz.D]
127.0.0.1  www.pheedo.com #[RSS Advertising]
127.0.0.1  ads.phillipsdata.us
127.0.0.1  www.phishingfix.biz #[Win32/TrojanClicker.VB.NP][server down?]
127.0.0.1  adclient.phoenixtv.com
127.0.0.1  ads.photosight.ru
127.0.0.1  phpadsnew.com
127.0.0.1  www.phpadsnew.com
127.0.0.1  www.picturecentre.com #[Win32/Agent.RC][Backdoor.Tricker]
127.0.0.1  ads.pimptel.com
127.0.0.1  banners.pinnaclesports.com
127.0.0.1  www.pkpsoft.com #[AdWare.Win32.SaveNow.bo][SiteAdvisor.pkpsoft.com]
127.0.0.1  ads.planetactive.com
127.0.0.1  ads.plantyours.com
127.0.0.1  banner.play-asia.com
127.0.0.1  ads2.playnet.com
127.0.0.1  xnrskh.plesse.hk #[Spamdexing]
127.0.0.1  counter.plugin.ws
127.0.0.1  www.plmq.com #[Exploit.ANI]
127.0.0.1  link.p0.com #[Web Bug][SiteAdvisor.p0.com]
127.0.0.1  cnt1.pocitadlo.cz
127.0.0.1  adserver.pollstar.com #[eTrust.Tracking.Cookie]
127.0.0.1  ad2.pop.com.br
127.0.0.1  nosex.pop3.ru #[Win32/Agent.OH]
127.0.0.1  qwekissme.pop3.ru #[Win32/Spy.Banker.BCK]
127.0.0.1  musicalcardss.pop3.ru #[Win32/Spy.Banker.BIG]
127.0.0.1  popfind.net #[Adware.Ddpop]
127.0.0.1  www.popupsandbanners.com #[TR/Amisa.A][Troj/Winsysba-G]
127.0.0.1  www.popupad.net #[SunBelt.PopUpAd]
127.0.0.1  www2.portdetective.com
127.0.0.1  ad2.postroller.com
127.0.0.1  ad3.postroller.com
127.0.0.1  www.ppctracking.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  adview.ppro.de
127.0.0.1  x0x0l.pp.ru #[BKDR_CCT.A]
127.0.0.1  adtxt.prbn.ru
127.0.0.1  ad468.prbn.ru
127.0.0.1  pr-cy.ru
127.0.0.1  www.praize.com #[Adware.Praize][SiteAdvisor.praize.com]
127.0.0.1  ads.premiumnetwork.net
127.0.0.1  ads.premiereinteractive.com
127.0.0.1  ads.primeinteractive.net
127.0.0.1  ads.prisacom.com #[RealMedia]
127.0.0.1  ad.pro-advertising.com
127.0.0.1  cdn1.pro-advertising.com
127.0.0.1  adv.profantasysports.com
127.0.0.1  profileawareness.com #[Trojan-Spy:JS/Spacestalk.A]
127.0.0.1  www.profilepeep.com #[MySpace Tracker]
127.0.0.1  ad.profiwin.de
127.0.0.1  bn.profiwin.de
127.0.0.1  www.promarketingclub.com
127.0.0.1  www.promobenef.com
127.0.0.1  www.prtracker.com
127.0.0.1  www.profitzone.com #[SunBelt.ProfitZONE Adbar]
127.0.0.1  www.promo.com.au
127.0.0.1  www.prutect.com #[Spyware.e2give][Win32.Prutec.A]
127.0.0.1  ad.prv.pl
127.0.0.1  www.psbill.biz
127.0.0.1  psefeed.com #[Spamdexing]
127.0.0.1  xml1.psefeed.com
127.0.0.1  www.psefeed.com
127.0.0.1  www.pstats.com
127.0.0.1  ads.psxextreme.com
127.0.0.1  pulsix.com #[maxalbums.com]
127.0.0.1  www.pulsix.com
127.0.0.1  www.puma163.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.puma164.com
127.0.0.1  ad.sma.punto.net
127.0.0.1  sma.punto.net
127.0.0.1  cgicounter.puretec.de
127.0.0.1  pynet.ws #[Spamdexing][server down?]
127.0.0.1  www.pynet.ws
# [Q]
127.0.0.1  www.q520.cn #[W32/Anivip]
127.0.0.1  exchange.qclix.com #[directtrack.com]
127.0.0.1  e1.cdn.qnsr.com
127.0.0.1  l1.cdn.qnsr.com #[WebBug]
127.0.0.1  adserv.quality-channel.de
127.0.0.1  qualityhitz.net
127.0.0.1  ads-205.quarterserver.de
127.0.0.1  ads.queendom.com
127.0.0.1  www.quickbar.co.kr #[eTrust.IEFilter.A]
127.0.0.1  deposito.quickstaraccess.com #[Win32/Diamin.NAF]
127.0.0.1  flat.quickstaraccess.com
127.0.0.1  antispyware.qmake.org
127.0.0.1  adsview.qq.com
127.0.0.1  adsview2.qq.com
127.0.0.1  www.qq886.com #[Backdoor.Semes]
127.0.0.1  quantserve.com
127.0.0.1  edge.quantserve.com
127.0.0.1  pixel.quantserve.com #[WebBug]
# [R]
127.0.0.1  ads.radioactive.se
127.0.0.1  ragazze-spiate.com
127.0.0.1  www.ragazze-spiate.com #[Trojan-Clicker.Win32.Agent.ip]
127.0.0.1  rainbow-mail.net #[Spamdexing]
127.0.0.1  clientreport.random-logic.com #[McAfee.Adware-CasOnline]
127.0.0.1  www.rankbooster.de
127.0.0.1  www.ranking-counter.de
127.0.0.1  realcrimea.info #[TR/Small.DBY.LH.12]
127.0.0.1  ads.recoletos.es
127.0.0.1  reportinstaller.random-logic.com
127.0.0.1  www.random-logic.com
127.0.0.1  ranking-hits.de
127.0.0.1  www.ranking-hits.de
127.0.0.1  counter.rapidcounter.com
127.0.0.1  www.rapidcounter.com
127.0.0.1  www.autoraskrutka.ru #[Spyware.Acext]
127.0.0.1  www.raskrutim.ru #[Spyware.Acext]
127.0.0.1  cnt.rate.ru
127.0.0.1  rb-net.com
127.0.0.1  count.rbc.ru
127.0.0.1  www.readnotify.com #[Email Tracker]
127.0.0.1  oasis.realbeer.com
127.0.0.1  www.realclicks.com
127.0.0.1  ads.reddit.com
127.0.0.1  ads.rediff.com
127.0.0.1  adworks.rediff.com
127.0.0.1  imadworks.rediff.com
127.0.0.1  www.redirad.de #[Adware.Redir]
127.0.0.1  js.redtram.com #[RedTramCookies]
127.0.0.1  js.en.redtram.com
127.0.0.1  referer.org
127.0.0.1  www.refer.ru
127.0.0.1  refferal.info #[Malicious.Links]
127.0.0.1  visit.referralware.com
127.0.0.1  regifast.com #[MVPS.Criteria][Adware.RegiFast]
127.0.0.1  www.regifast.com #[Trojan.RegiFast]
127.0.0.1  ads.register.com
127.0.0.1  www.registrarads.com
127.0.0.1  www.registrysweeper.com #[Symantec.RegistrySweeper]
127.0.0.1  include.reinvigorate.net
127.0.0.1  stats.reinvigorate.net #[WebBug]
127.0.0.1  counter.relmaxtop.com
127.0.0.1  www.relmaxtop.com
127.0.0.1  banner.relcom.ru
127.0.0.1  www.rentyourdot.com
127.0.0.1  dn.research-int.se #[Insight XE TAGGING]
127.0.0.1  flnet.research-int.se
127.0.0.1  sn.research-int.se
127.0.0.1  tradera.research-int.se
127.0.0.1  dae.responsetarget.com #[AutoGK][IE-SpyAd][MVPS.Criteria]
127.0.0.1  banners.resultonline.com
127.0.0.1  www.returnreceipt.com #[Email Tracker]
127.0.0.1  www.results-google.info #[Spamdexing]
127.0.0.1  000dom.revenuedirect.com
127.0.0.1  cache.revenuedirect.com #[Parking Service]
127.0.0.1  traffic.revenuedirect.com
127.0.0.1  traffic.beta.revenuedirect.com
127.0.0.1  click.revenuepilot.com
127.0.0.1  search.revenuepilot.com
127.0.0.1  ads.revenews.com
127.0.0.1  www.reversecontext.com
127.0.0.1  ads.reviewcentre.com
127.0.0.1  revolt-search.com #[Spamdexing]
127.0.0.1  www.revresda.com
127.0.0.1  tds.revsp.com #[WinFixer]
127.0.0.1  webtrends.reynoldswebsolutions.com #[hitbox.com]
127.0.0.1  ad.rd06.com
127.0.0.1  r.rd06.com
127.0.0.1  right-search.org #[Spamdexing]
127.0.0.1  rightstats.com
127.0.0.1  www.rightstats.com
127.0.0.1  install1.ring520.org #[Trojan.Farfli]
127.0.0.1  install2.ring520.org
127.0.0.1  install3.ring520.org
127.0.0.1  install4.ring520.org
127.0.0.1  www.ritztours.com #[Backdoor.Win32.Bifrose.kt]
127.0.0.1  rc.rizalof.com #[Win32/Boxed.BY][TR/Proxy.Horst.bl]
127.0.0.1  m.rmbclick.com
127.0.0.1  robotraff.com #[Malicious.Links]
127.0.0.1  roia.biz
127.0.0.1  backoffice.roitracking.info
127.0.0.1  tracking.vx.roo.com
127.0.0.1  show.roogoo.com
127.0.0.1  www.roogoo.com #[Adware.Roogoo]
127.0.0.1  banner.royaldice.com
127.0.0.1  www.rgs-rostock.de #[Trojan.Mitglieder.C][Backdoor.Gaster]
127.0.0.1  serving.rpowermedia.com #[AdvertPro]
127.0.0.1  ldkiekxc.rr.nu #[Backdoor.Ryejet.B]
127.0.0.1  upd.rssservice.net #[Trojan-Downloader.Win32.Small.cug]
127.0.0.1  update.rssservice.net
127.0.0.1  ru-traffic.com
127.0.0.1  banners.rushcommerce.com
127.0.0.1  www.rwvwv.com #[Javascript.Exploit]
# [S]
127.0.0.1  sss.s200.cn #[Javascript.Exploit]
127.0.0.1  amp.st.sageanalyst.net
127.0.0.1  matchnet.st.sageanalyst.net #[McAfee.Cookie-Sageanalyst]
127.0.0.1  st.sageanalyst.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  salevisitor.net
127.0.0.1  judo.salon.com
127.0.0.1  oas.salon.com
127.0.0.1  www.sapium.com #[NOD32.Win32/Spy.Banker.AHY]
127.0.0.1  tvinterativa.paginas.sapo.pt #[Win32/Spy.Banker.AHY]
127.0.0.1  sandracounter.com #[Trojan-Downloader.Win32.Agent.bhg]
127.0.0.1  ads.sapo.pt
127.0.0.1  statisfy.net
127.0.0.1  banner.sayt.ws
127.0.0.1  www.sb165138.com #[Javascript.Exploit]
127.0.0.1  scaredback.com #[PWSteal.Tarno.R][Downloader-ATM]
127.0.0.1  banner.scasino.com #[AdWare.Win32.Casino.w]
127.0.0.1  adserver.scivista.com
127.0.0.1  scorpionsearch.com #[W32.Adclicker.C.Trojan]
127.0.0.1  www.scorpionsearch.com #[x10.com][Trojan.Clicker.NetBuie a-b]
127.0.0.1  www.scratchindian.com #[Backdoor.Samkams]
127.0.0.1  adsremote.scripps.com #[McAfee.Cookie-Scripps]
127.0.0.1  railads.scripps.com
127.0.0.1  te.scripps.com
127.0.0.1  horyzonix.sdv.fr #[RealMedia]
127.0.0.1  www.se911.com #[Win32/PSW.Legendmir.ATE]
127.0.0.1  s-e-arch.com #[server down?]
127.0.0.1  search2007.info #[Spamdexing]
127.0.0.1  search4fast.com #[Spamdexing]
127.0.0.1  search4top.com
127.0.0.1  www.search4top.com
127.0.0.1  ads.search.bg
127.0.0.1  banner.search.bg
127.0.0.1  banex.search.bg
127.0.0.1  counter.search.bg
127.0.0.1  ads.searchextreme.com
127.0.0.1  searchfirst10.info #[Malicious.Links]
127.0.0.1  ad.searchhound.com
127.0.0.1  www.searchithere.net #[Spamdexing]
127.0.0.1  searchitquick.com
127.0.0.1  tb.searchitquick.com
127.0.0.1  www.searchitquick.com #[SunBelt.SearchItQuick Toolbar]
127.0.0.1  www.searchlab.info #[Spamdexing]
127.0.0.1  www.searchmachine.com
127.0.0.1  tracking.searchmarketing.com
127.0.0.1  www.searchrelevancy.com #[Spyware.Relevancy]
127.0.0.1  search-vip.net
127.0.0.1  www.searchvivor.com #[McAfee.Adware-DCToolbar]
127.0.0.1  secbash.biz #[Malicious.Links][server down?]
127.0.0.1  dl.secondsite2.com
127.0.0.1  img.secondsite2.com #[Web-Attacker Control panel]
127.0.0.1  www.img.secondsite2.com #[Win32/TrojanDownloader.Small.NFP]
127.0.0.1  www.secondsite2.com
127.0.0.1  secondwww.com
127.0.0.1  www.secureappz.com #[Trojan.TrustedZone]
127.0.0.1  plugin.secureservicepack.com #[HJTH.GoDOTLess]
127.0.0.1  images-pw.secureserver.net #[Parking Service][GoDaddy]
127.0.0.1  images.secureserver.net
127.0.0.1  imagesak.secureserver.net
127.0.0.1  adserver.securityfocus.com #[RealMedia]
127.0.0.1  www.selfsurveys.com
127.0.0.1  www.seehits.com
127.0.0.1  ads.seekingalpha.com
127.0.0.1  sellbuytraff.com #[freescanpro.com]
127.0.0.1  www.send-safe.com #[Spamware]
127.0.0.1  www.senlove.com #[Trojan-Downloader:HTML/Agent.DY]
127.0.0.1  ad.sensismediasmart.com.au
127.0.0.1  seodrugs.com #[Spamdexing]
127.0.0.1  seoexp.info #[Spamdexing]
127.0.0.1  stats.seostats.com
127.0.0.1  serialkey.net #[Kephyr.PUP]
127.0.0.1  www.serialkey.net
127.0.0.1  www.serveads.com
127.0.0.1  zero.serverc.org #[Win32.Trojan-Downloader.Alphabet.GEN]
127.0.0.1  setlee.org #[Spamdexing]
127.0.0.1  pix.sexyads.net
127.0.0.1  www.sexyads.net #[SunBelt.SexyAds.net]
127.0.0.1  ad.seznam.cz
127.0.0.1  ads.shopthescene.com
127.0.0.1  ads.shoutfile.com
127.0.0.1  sincooweb.com #[Backdoor.Graybird.N]
127.0.0.1  www.slacker24.com #[Win32/Spy.Banker.AHY]
127.0.0.1  ads2.slickdeals.net
127.0.0.1  update.smartallyes.com #[Trojan.Smartallyes]
127.0.0.1  adimages.sina.com.hk
127.0.0.1  jsads.sina.com.hk
127.0.0.1  startpunt.nu.site-id.nl
127.0.0.1  www.sismodular.com #[Win32/Eyeveg.T]
127.0.0.1  www.site-id.nl
127.0.0.1  tracker.sitescout.com
127.0.0.1  carde.sitesled.com #[Win32/Spy.Banker.ANV]
127.0.0.1  advertpro.sitepoint.com
127.0.0.1  www.sitestatslive.com
127.0.0.1  www.sitewebstats.com
127.0.0.1  ads.sixapart.com
127.0.0.1  adserver.sharewareonline.com #[nictechnetworks.com]
127.0.0.1  ads.shizmoo.com #[Kephyr.PUP]
127.0.0.1  shojacash.ws #[Win32/Spy.Banker.CKW]
127.0.0.1  www.shockcounter.com
127.0.0.1  ads.sina.com
127.0.0.1  www.skeech.com #[SunBelt.Skeech]
127.0.0.1  go.skins.be
127.0.0.1  screensavers.skins.be #[Win32/Adware.Stud]
127.0.0.1  www.skins.be
127.0.0.1  oas.skyregie.com #[RealMedia]
127.0.0.1  www.sl952571.cn #[Google.Warning]
127.0.0.1  www.small-tool.net #[Monitor.Win32.RemoteWatch.a]
127.0.0.1  www.smalltool.net #[Adware/LoopAd]
127.0.0.1  www.smartadserver.com #[SunBelt.SmartAdServer.com]
127.0.0.1  smart-browser.com #[eTrust.SmartBrowser]
127.0.0.1  update.smart-browser.com #[SunBelt.SmartBrowser]
127.0.0.1  www.smart-browser.com #[Adware.SmartBrowser]
127.0.0.1  www.smileyworld.com #[AdWare.Win32.SHBar.a][Adware.Smiley]
127.0.0.1  ads.sn.se
127.0.0.1  pub.softonic.com
127.0.0.1  update.cpc.sogou.com #[Adware.CPush]
127.0.0.1  ads.sopeng.com #[Adware.CPush]
127.0.0.1  a.sou7.com #[NOD32.NewHeur_PE]
127.0.0.1  ivox.socratos.net
127.0.0.1  www.softwareclub.ws #[Adware.SaveNow]
127.0.0.1  a.softpedia.com
127.0.0.1  adserver.softwareonline.com
127.0.0.1  www.someads.com
127.0.0.1  soso32.org #[Javascript.Exploit]
127.0.0.1  www1.spaex.com #[searchboss.com]
127.0.0.1  www.specialstat.com
127.0.0.1  www.spedia.net #[SunBelt.SpediaBar][Adware.Spedia]
127.0.0.1  speedsearcher.net #[Spamdexing][Microsoft.Strider]
127.0.0.1  www.speedtracker.de
127.0.0.1  stats.sphere.com
127.0.0.1  www.sponsorads.de
127.0.0.1  sitestat3.sport1.de
127.0.0.1  www.spamcatchero.biz #[Backdoor.Mydopam]
127.0.0.1  www.speedcounter.net
127.0.0.1  ads-fr.spray.net #[SpySweeper.Spy.Cookie]
127.0.0.1  www.spyarsenal.com #[Spyware.DesktopSpy][Spyware.FamilyKeylog]
127.0.0.1  spybiz4u.com #[Trojan.Win32.Agent.afw]
127.0.0.1  www.spybiz4u.com
127.0.0.1  cracks.spb.ru #[Win32/TrojanDownloader.Adload.DS]
127.0.0.1  v.sodui.com
127.0.0.1  www.sodui.com #[Adware.SoduiSearch]
127.0.0.1  www.srchtop.com #[Spamdexing]
127.0.0.1  www.stacy-keibler-pictures.com #[Malicious.Links.Zango]
127.0.0.1  bannerads.standard.net
127.0.0.1  ads.starpulse.com #[SpySweeper.Spy.Cookie]
127.0.0.1  0.start.bz #[Trojan-Downloader.Win32.Small.dxg]
127.0.0.1  www.startsurfing.com #[McAfee.Adware-StartSurfing]
127.0.0.1  ads.stardoll.com
127.0.0.1  stat.stars.ru #[WebBug]
127.0.0.1  adsintl.starwave.com
127.0.0.1  active.hit.stat24.com
127.0.0.1  lt3.hit.stat24.com
127.0.0.1  s4.hit.stat24.com
127.0.0.1  ua1.hit.stat24.com
127.0.0.1  www.stat24.com
127.0.0.1  js.statistici.ro
127.0.0.1  log.statistici.ro
127.0.0.1  s.statistici.ro
127.0.0.1  storage.statistici.ro
127.0.0.1  hitx.statistics.ro
127.0.0.1  statistik-gallup.net
127.0.0.1  s-t-a-t-s.com
127.0.0.1  www.stats4free.de
127.0.0.1  stats4you.com
127.0.0.1  reg.stats4all.com
127.0.0.1  www.stats4you.com
127.0.0.1  stat.statistiche.ws
127.0.0.1  www.statistiche.ws
127.0.0.1  log3.stats24.net
127.0.0.1  www.statsmachine.com
127.0.0.1  www.statsector.hu
127.0.0.1  statswhere.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.stattrax.com
127.0.0.1  i.stealfrommvps.org
127.0.0.1  step57.com
127.0.0.1  cleo.step57.com
127.0.0.1  me.step57.com #[Google.Warning]
127.0.0.1  rus.step57.com
127.0.0.1  traff.step57.com
127.0.0.1  ads.stopbounce.com
127.0.0.1  tac.ads.streamtheworld.com
127.0.0.1  cbs.ads.streamtheworld.com
127.0.0.1  ads.tetesacl.streamtheworld.com
127.0.0.1  www.stickypops.com #[eTrust.Stickypops]
127.0.0.1  gsorder.berlin.strato.de
127.0.0.1  www.streamxs.ws #[Trojan-Downloader.Win32.Tiny.dk]
127.0.0.1  adult.stylishvideo.com
127.0.0.1  top.stylishvideo.com #[Malicious.Links]
127.0.0.1  sex.stylishvideo.com
127.0.0.1  www.stylishvideo.com
127.0.0.1  www.sublimemedia.net
127.0.0.1  counter.surfcounters.com
127.0.0.1  super-contenuti.com
127.0.0.1  www.super-contenuti.com
127.0.0.1  clix.superclix.de
127.0.0.1  www.superclix.de
127.0.0.1  banner.supereva.it
127.0.0.1  ww2.superguadagni.net
127.0.0.1  www.superlogy.com #[AdvWare.ToolBar.VB.b][Adware.Superlogy]
127.0.0.1  adidm.supermedia.pl
127.0.0.1  super-portal.info
127.0.0.1  stat.superstat.info
127.0.0.1  www.superstat.info
127.0.0.1  adsuccess.surehits.com
127.0.0.1  adv.surinter.net
127.0.0.1  rd1.surfernetwork.com #[SurferNETWORK Plugin]
127.0.0.1  www.surfernetwork.com
127.0.0.1  www.surveynetworks.com
127.0.0.1  sutds.info
127.0.0.1  suwage.info #[Malicious.Links]
127.0.0.1  ads.svnt.com
127.0.0.1  www.sweet-cindy.info #[Spamdexing]
127.0.0.1  swkee.com #[Google.Warning]
127.0.0.1  adpick.switchboard.com
127.0.0.1  www.syamantec.com #[Typo Squatter][gotoo.com]
127.0.0.1  antispam.symlinks.org #[SpamBot]
127.0.0.1  adtag.sympatico.ca
127.0.0.1  www.system4.nl
127.0.0.1  sysregistry.com #[McAfee.FakeAlert-H]
127.0.0.1  www.sysregistry.com #[Prevx1.Malware:SysCovert]
# [T]
127.0.0.1  vip3.t2t2.com
127.0.0.1  vip5.t2t2.com
127.0.0.1  freeware-ad.t35.com #[umaxsearch.com]
127.0.0.1  hkvn99.t35.com
127.0.0.1  ijj.t35.com #[W32/Bagle.HQ][Wildcard DNS]
127.0.0.1  kuringao.t35.com #[Win32/TrojanDownloader.Banload.BDJ]
127.0.0.1  nolko.t35.com
127.0.0.1  spyware-re.t35.com #[umaxsearch.com]
127.0.0.1  ud7swe.t35.com #[W32.Dinoxi][W32/Style-A]
127.0.0.1  vbs.t35.com
127.0.0.1  wmeg.t35.com #[Spamdexing]
127.0.0.1  bs.t-redirect.com #[Google.Warning]
127.0.0.1  tabletsa.net #[Spamdexing]
127.0.0.1  www.tabletsa.net
127.0.0.1  www.tagexplosion.com #[AdWare.Win32.Eztracks.b]
127.0.0.1  ads.tagword.com
127.0.0.1  takesnames.info #[Javascript.Exploit][server down?]
127.0.0.1  ad.uk.tangozebra.com
127.0.0.1  www.tankersite.com
127.0.0.1  dev.targetpoint.com
127.0.0.1  srs.targetpoint.com
127.0.0.1  targettraf.com
127.0.0.1  stat-counter.tass-online.ru
127.0.0.1  tat-neftbank.ru #[Backdoor.Berbew.H]
127.0.0.1  ad.tbn.ru
127.0.0.1  ad.ent.tbn.ru
127.0.0.1  ad.gen.tbn.ru
127.0.0.1  ad.100.tbn.ru
127.0.0.1  ad.120-gen.tbn.ru
127.0.0.1  ad.strict.tbn.ru
127.0.0.1  ad.text-ent.tbn.ru
127.0.0.1  ad.text.tbn.ru
127.0.0.1  www.tdstats.com
127.0.0.1  tdstar.info #[Spamdexing]
127.0.0.1  t-error.biz
127.0.0.1  www.t-error.biz
127.0.0.1  www.tech-counter.com
127.0.0.1  banner.techarp.com
127.0.0.1  www.teligo-ads.de
127.0.0.1  navx3.tempdomainname.com #[SiteAdvisor.totallyfreegames.com]
127.0.0.1  www.tencent.com #[Backdoor.Prosti]
127.0.0.1  www.tenmonkey.com
127.0.0.1  adserver.teracent.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  adserver2.teracent.net
127.0.0.1  adserver1.teracent.net
127.0.0.1  adserver.terra.es
127.0.0.1  dy.testnet.nl
127.0.0.1  textad.net
127.0.0.1  www.textads.biz
127.0.0.1  www.textlink.cn
127.0.0.1  www.textlink.cz
127.0.0.1  www.text-link-ads.com
127.0.0.1  www.textlinkads.com
127.0.0.1  tdsru.info #[Spamdexing]
127.0.0.1  openad.tf1.fr #[RealMedia]
127.0.0.1  openadext.tf1.fr
127.0.0.1  a.tfag.de
127.0.0.1  ak.tfag.de
127.0.0.1  theaffiliateprogram.com
127.0.0.1  ads.the-bikini.com
127.0.0.1  thecoolpics.com #[W32.Imaut.J]
127.0.0.1  ads.thegauntlet.com
127.0.0.1  thegiants.info
127.0.0.1  thegoodfind.com
127.0.0.1  www.thegoodfind.com
127.0.0.1  www.thekurt.info #[Javascript.Exploit][server down?]
127.0.0.1  ads.the-lingerie-post.com
127.0.0.1  dclk.themarker.com
127.0.0.1  adbot.theonion.com
127.0.0.1  www.thepokerclub.com #[SecurityRisk.ClubPoker]
127.0.0.1  therichmedia.com
127.0.0.1  r.the-search.us #[Spamdexing]
127.0.0.1  www.theserials.com #[Google.Warning]
127.0.0.1  www.thevipsearch.com #[Spamdexing]
127.0.0.1  ad.thinkmedia.cn
127.0.0.1  webtrends.thisis.co.uk #[Hitbox]
127.0.0.1  oas.tidningsnatet.se #[ads.realmedia.basefarm.net]
127.0.0.1  www.ting789.com #[McAfee.StartPage-HR]
127.0.0.1  www.tinka.ru
127.0.0.1  mycounter.tinycounter.com
127.0.0.1  ad.tiscali.com
127.0.0.1  ad-cz.tiscali.com
127.0.0.1  ad-de.tiscali.com
127.0.0.1  ad-it.tiscali.com
127.0.0.1  ad-nl.tiscali.com
127.0.0.1  ad-sc.tiscali.com
127.0.0.1  ad-uk.tiscali.com
127.0.0.1  sitestats.tiscali.co.uk #[WebBug]
127.0.0.1  adsweb.tiscali.cz
127.0.0.1  adsweb.tiscali.it #[Accipiter]
127.0.0.1  titlefun.info #[Spamdexing]
127.0.0.1  ads.as4x.tmcs.net
127.0.0.1  ads.tm-research.com
127.0.0.1  tnc4u.com
127.0.0.1  new.tnc4u.com
127.0.0.1  www.tnc4u.com #[Adware.DownloadPlus]
127.0.0.1  tns-counter.ru
127.0.0.1  www.tns-counter.ru
127.0.0.1  toastystfc.com #[umax]
127.0.0.1  ads.tolshop.com
127.0.0.1  ad.tom.com
127.0.0.1  flashad.tom.com
127.0.0.1  usmsad.tom.com
127.0.0.1  ww1.tongji123.com
127.0.0.1  ww2.tongji123.com
127.0.0.1  ww3.tongji123.com
127.0.0.1  ww4.tongji123.com
127.0.0.1  banner.tonygpoker.com
127.0.0.1  cachebanner.tonygpoker.com
127.0.0.1  counter.top.ge
127.0.0.1  top10profit.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.top100.lt
127.0.0.1  www.topbestsites.net #[Spamdexing]
127.0.0.1  hit.topc.org
127.0.0.1  banners.topcities.com
127.0.0.1  toplist.cz
127.0.0.1  www.toplist.cz
127.0.0.1  counter.topphoto.ru
127.0.0.1  www.music.topsearch20.net #[Spamdexing]
127.0.0.1  a.total-media.net
127.0.0.1  i.total-media.net
127.0.0.1  log.traceics.ca
127.0.0.1  storage.traceics.ca
127.0.0.1  webads.tradeholding.com
127.0.0.1  traffmanager.org #[Javascript.Exploit]
127.0.0.1  log.trafic.ro
127.0.0.1  storage.trafic.ro
127.0.0.1  track.trafiz.net
127.0.0.1  adserv.transindex.ro
127.0.0.1  top50sites.info #[Spamdexing]
127.0.0.1  ads.topix.net
127.0.0.1  ad.topstat.com
127.0.0.1  nl.topstat.com
127.0.0.1  s26.topstat.com
127.0.0.1  xl.topstat.com
127.0.0.1  total-search.info #[ISANS.Alert]
127.0.0.1  banners.toteme.com
127.0.0.1  cachebanners.toteme.com
127.0.0.1  trackalyzer.com
127.0.0.1  t2.trackalyzer.com
127.0.0.1  t4.trackalyzer.com
127.0.0.1  ads.track-star.com #[SunBelt.Track-Star.com]
127.0.0.1  adserver.track-star.com
127.0.0.1  www.track-star.com
127.0.0.1  tracksy.com
127.0.0.1  ads.tradermedia.co.uk
127.0.0.1  rotator.tradetracker.nl
127.0.0.1  ti.tradetracker.nl
127.0.0.1  adserver.tradingmarkets.com
127.0.0.1  www.trafficcenter.de
127.0.0.1  traffic-converter.biz
127.0.0.1  textad.traficdublu.ro
127.0.0.1  www.traffds.net
127.0.0.1  www.trafficmasterz.net
127.0.0.1  s2.trafficmaxx.de
127.0.0.1  s3.trafficmaxx.de
127.0.0.1  traffloads.com
127.0.0.1  ads.traderonline.com #[RealMedia]
127.0.0.1  www.traffic4u.com
127.0.0.1  traffic-acc.com #[Spyware.TrafficAccProc]
127.0.0.1  www.trafficbeamer.com
127.0.0.1  www.trafficbeamer.nl
127.0.0.1  trafficg.com
127.0.0.1  www.trafficg.com
127.0.0.1  trafficfile.com
127.0.0.1  www.trafficfile.com
127.0.0.1  www.trafficflame.com
127.0.0.1  trafficflare.com
127.0.0.1  cnt.trafficvalet.com
127.0.0.1  www.trafficzap.com
127.0.0.1  trackyourstats.com
127.0.0.1  www.trackyourstats.com
127.0.0.1  hit.traxdb.net
127.0.0.1  media.travelzoo.com
127.0.0.1  media2.travelzoo.com
127.0.0.1  ads.triada.bg
127.0.0.1  adserver.tripsmarter.com
127.0.0.1  trudomain.com
127.0.0.1  www.trudomain.com #[Javascript.Exploit]
127.0.0.1  truefindpage.com
127.0.0.1  hits.truehits.in.th
127.0.0.1  lvs.truehits.in.th
127.0.0.1  tracker.truehits.in.th
127.0.0.1  hits3.truehits.net
127.0.0.1  tracker.truehits.net
127.0.0.1  www.trusttoolbar.com #[eTrust.Trust Toolbar]
127.0.0.1  trywith.us #[Spamdexing]
127.0.0.1  www.tscounter.com
127.0.0.1  adclient1.tucows.com
127.0.0.1  counts.tucows.com
127.0.0.1  google.tucows.com
127.0.0.1  icornerstore.tumri.net #[TumriAds]
127.0.0.1  images.tumri.net
127.0.0.1  www.tumri.net
127.0.0.1  www.turls.info
127.0.0.1  ad.turn.com
127.0.0.1  tv-eg.com #[AdWare.Win32.Softomate.x]
127.0.0.1  ad.tv2.no #[RealMedia]
127.0.0.1  tvbad1.tvb.com
127.0.0.1  ads.tweakxp.com
127.0.0.1  down.tygzs.cn #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  ads1.tyroo.com
127.0.0.1  ads5.tyroo.com
127.0.0.1  ads6.tyroo.com
127.0.0.1  serve.tyroo.com
# [U]
127.0.0.1  u2malaysia.com #[Javascript.Exploit]
127.0.0.1  mde.ubid.com #[RealMedia]
127.0.0.1  ads.ucomics.com #[RealMedia]
127.0.0.1  image.ugo.com
127.0.0.1  mediamgr.ugo.com #[McAfee.Cookie-UGOr]
127.0.0.1  deliver.ads.uigc.net #[RealMedia]
127.0.0.1  creativos.ads.uigc.net
127.0.0.1  ip2k.ads.uigc.net
127.0.0.1  adclient.uimserv.net
127.0.0.1  adimg.uimserv.net
127.0.0.1  www.ukbanners.com
127.0.0.1  www.ultimatetopsites.com
127.0.0.1  file.unionsms.net #[Win32/TrojanDownloader.QQHelper.NAF][server down?]
127.0.0.1  universaltoolbar.com #[AdWare.Win32.Simbar.e]
127.0.0.1  www.unlimits.net #[Javascript.Exploit]
127.0.0.1  ads.unlimitedbanners.com
127.0.0.1  undertonenetworks.com #[zedo.com]
127.0.0.1  www.undertonenetworks.com
127.0.0.1  managed.unexpand.com
127.0.0.1  update.unexpand.com #[SpamBot]
127.0.0.1  update.unflatten.com
127.0.0.1  ads.unison.ie
127.0.0.1  ads.universia.com.br
127.0.0.1  ads.univision.com
127.0.0.1  web.unltd.info
127.0.0.1  cyclops.prod.untd.com #[RealMedia]
127.0.0.1  nztv.prod.untd.com
127.0.0.1  track.untd.com
127.0.0.1  ads1.updated.com
127.0.0.1  www.uplink.co.kr #[Adware.Uplink]
127.0.0.1  www.upspiral.com #[Adware.UpSpiralBar]
127.0.0.1  www.urpo.com #[SunBelt.Urpo]
127.0.0.1  banner.usacasino.com
127.0.0.1  usachoice.net
127.0.0.1  usamedfarm.biz #[Spamdexing]
127.0.0.1  ads.userfriendly.org #[AdvertPro]
127.0.0.1  adsnew.userfriendly.org
127.0.0.1  m.usersonline.com #[WebBug]
127.0.0.1  www.usersonlinecounter.com
127.0.0.1  ads.ussearch.com
127.0.0.1  www.utarget.co.uk #[utarget Ad code]
127.0.0.1  rotabanner100.utro.ru
127.0.0.1  traffic.uusee.com
127.0.0.1  ads.ux-tm.net
127.0.0.1  hit.ux-tm.net
127.0.0.1  top.ux-tm.net
# [V]
127.0.0.1  beacon.valeoip.com
127.0.0.1  feed.validclick.com
127.0.0.1  ad.jp.ap.valuecommerce.com #[SecuritySpace.WebBug]
127.0.0.1  ad.valuehost.ru
127.0.0.1  ad.vba.ru
127.0.0.1  vcodec2007.com
127.0.0.1  www.vcodec2007.com
127.0.0.1  tds.verrm.org #[SiteAdvisor.msiesettings.com]
127.0.0.1  publicidad.vocento.com
127.0.0.1  ads.vegas.com
127.0.0.1  ad.vel.pl
127.0.0.1  counters.vendio.com
127.0.0.1  ads.vertele.com
127.0.0.1  www.verticlick.com
127.0.0.1  spinbox.versiontracker.com #[McAfee.Cookie-Versiontrack]
127.0.0.1  www.view4cash.de
127.0.0.1  web.vindicosuite.com #[WebBug]
127.0.0.1  ringtones-vip.org #[IFrame.Exploit]
127.0.0.1  search-vip.org #[Spamdexing]
127.0.0.1  banners.vipprofits.com
127.0.0.1  www.vistachecker.com #[Backdoor.Toob.B][server down?]
127.0.0.1  sniff.visistat.com
127.0.0.1  wp.vizu.com
127.0.0.1  ads.v-links.net
127.0.0.1  voena.net #[Google.Warning]
127.0.0.1  www.voonda.com #[Spyware.TAFbar]
127.0.0.1  ads2.vortexmediagroup.com #[AdvertPro]
127.0.0.1  vote4warez.com
127.0.0.1  www.vstats.net
127.0.0.1  sevenc.vze.com #[VBS.Powcox@mm]
# [W]
127.0.0.1  w32-gen.net #[Exploit.HTML.IESlice.d]
127.0.0.1  www.w3exit.com
127.0.0.1  www.wallpapergate.com #[Malicious.Content.Zango]
127.0.0.1  ad.wanderlist.com
127.0.0.1  wants-search.com
127.0.0.1  www.warezenergy.com #[Adware.Begin2search]
127.0.0.1  ng3.ads.warnerbros.com
127.0.0.1  traffic.waypointcash.com #[server down?]
127.0.0.1  ads.weather.ca
127.0.0.1  btn.counter.weather.ca
127.0.0.1  twnads.weather.ca
127.0.0.1  ads.weather.com
127.0.0.1  pub.weatherbug.com #[RealMedia]
127.0.0.1  100webads.com
127.0.0.1  tracking.web2corp.com
127.0.0.1  adserver.webads.it
127.0.0.1  images.webads.it
127.0.0.1  data.webads.co.nz
127.0.0.1  ad.webadvertising.ch
127.0.0.1  adv.webadvertising.ch
127.0.0.1  nx-adv.webadvertising.ch #[RealMedia]
127.0.0.1  c.webbuying.net
127.0.0.1  s.webbuying.net #[Adware-WebBuying]
127.0.0.1  www.webbuying.net
127.0.0.1  www.web-chart.de
127.0.0.1  blog1000.webcindario.com #[Win32/Spy.Banker.AWA]
127.0.0.1  horoscoponetvirt.webcindario.com #[Win32/Spy.Banker.BFW]
127.0.0.1  voxcartao.webcindario.com #[Win32/Spy.Banker.Big]
127.0.0.1  www.wecounthits.com
127.0.0.1  webcounter.be
127.0.0.1  webcounter.com
127.0.0.1  www.webcounter.com
127.0.0.1  www.webhits.de
127.0.0.1  www.weblogtracker.net
127.0.0.1  banners.webmasterplan.com #[SecuritySpace.WebBug]
127.0.0.1  partners.webmasterplan.com
127.0.0.1  fc.webmasterpro.de
127.0.0.1  adv.webmd.com
127.0.0.1  webhits.de
127.0.0.1  stat.webmedia.pl
127.0.0.1  bannervip.web1000.com
127.0.0.1  ads.webads360.com
127.0.0.1  advertpro.webspawner.com
127.0.0.1  img.webring.com #[SecuritySpace.WebBug]
127.0.0.1  img1.webring.com
127.0.0.1  ss.webring.com
127.0.0.1  track.websitetrafficreport.com #[VisitorTrack Code]
127.0.0.1  5623.web-stats.org
127.0.0.1  www.webstat.net
127.0.0.1  www.webstat.se
127.0.0.1  fry.webtistic.com
127.0.0.1  www.webtistic.com
127.0.0.1  ads.webtools24.net
127.0.0.1  banner.webtools24.net
127.0.0.1  toolbar.webtoolbars.com
127.0.0.1  web-url.de #[SANS.Alert][Trojan.Muldrop]
127.0.0.1  www.web-url.de
127.0.0.1  ad.wedoo.com
127.0.0.1  adserver.wenters.com
127.0.0.1  www.werevolf.info #[Javascript.Exploit.makemelaugh]
127.0.0.1  werew0lf.net #[Trojan-PSW.Win32.LdPinch.bio]
127.0.0.1  www.werew0lf.net
127.0.0.1  banner.westernunion.com
127.0.0.1  wethere.com
127.0.0.1  www.wethere.com #[Malicious.Links.lop.com]
127.0.0.1  partner1.whatsfind.com
127.0.0.1  www.whatsfind.com #[HTML_STARTPAGE.C]
127.0.0.1  www.whatsthatcode.com #[Malicious.Links.Zango]
127.0.0.1  wikia-ads.wikia.com
127.0.0.1  oasads.whitepages.com #[RealMedia]
127.0.0.1  tracker.wholinked.com
127.0.0.1  whoisonline.net
127.0.0.1  cache.winhundred.com
127.0.0.1  join1.winhundred.com
127.0.0.1  join2.winhundred.com
127.0.0.1  secure.winhundred.com
127.0.0.1  www.winhundred.com #[SiteAdvisor.winhundred.com]
127.0.0.1  window1.com #[IE-SpyAd]
127.0.0.1  ads1.winhelp2002.net
127.0.0.1  www.winneronline.ru #[Javascript.Exploit]
127.0.0.1  top.winrate.net
127.0.0.1  stats.wired.com
127.0.0.1  www.wisecounter.com
127.0.0.1  ads.winsite.com
127.0.0.1  winsoftwareupdate.org #[Trojan.Renver]
127.0.0.1  win-spy.com
127.0.0.1  www.win-spy.com #[eTrust.Win-Spy][Spyware.WinSpy]
127.0.0.1  winstream.com #[Parasite.Searchex]
127.0.0.1  www.winstream.com
127.0.0.1  clicktrack.wnu.com
127.0.0.1  www.world-banners.com
127.0.0.1  world0fwarcraft.net #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.wor1dofwar.net #[Javascript.Exploit]
127.0.0.1  www.wor1dofwarcraft.com #[Javascript.Exploit]
127.0.0.1  stats.wordpress.com
127.0.0.1  analytics.worldnow.com #[WebBug]
127.0.0.1  wtsdc.worldnow.com #[WebTrends]
127.0.0.1  www.worlds-best-online-casinos.com #[AdWare.Win32.Casino.w]
127.0.0.1  ads.worthplaying.com
127.0.0.1  www.wowchian.com #[Win32/PSW.Lineage.DN][W32.Looked.P]
127.0.0.1  www.wowrelax.com #[Spamdexing]
127.0.0.1  wowsearch.org
127.0.0.1  www.wowsearch.org
127.0.0.1  www.wowweb.net #[Adware.WWWBar]
127.0.0.1  adsearch.wp.pl
127.0.0.1  adv.wp.pl
127.0.0.1  badv.wp.pl
127.0.0.1  dot.wp.pl #[WebBug]
127.0.0.1  ad.wretch.cc
127.0.0.1  www.wvyi.com #[Javascript.Exploit]
127.0.0.1  oas.wwwheise.de #[RealMedia]
127.0.0.1  www.wwppc.com #[Spamdexing]
127.0.0.1  www-hinet.net #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  ad.wz.cz
127.0.0.1  cc.wzxqy.com #[Win32/PSW.QQPass.VD]
# [X]
127.0.0.1  x-antrian.com #[Malicious.Links]
127.0.0.1  ads.xboxic.com
127.0.0.1  xcounters.com
127.0.0.1  a.xcounters.com
127.0.0.1  www.xexe.info #[MHTMLRedir.Exploit]
127.0.0.1  count.xhit.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  nedstats.xs4all.nl
127.0.0.1  gostosa01.xpg.com.br #[Win32/Spy.Banker.ANV]
127.0.0.1  www.repressaoaocrime.xpg.com.br #[Win32/Spy.Banker.ANV]
127.0.0.1  new.xp-antispyware.com
127.0.0.1  update.xp-antispyware.com #[SpamBot]
127.0.0.1  xtainment.net
127.0.0.1  ads.xtra.co.nz
127.0.0.1  xuixui.net #[Spamdexing.Malicious.Links]
# [Y]
127.0.0.1  ads.yadio.com
127.0.0.1  dl.yadio.com
127.0.0.1  www.yadio.com
127.0.0.1  ad.yadro.ru #[SpySweeper.Spy.Cookie]
127.0.0.1  counter.yadro.ru #[McAfee.Cookie-Yadro][Panda.Spyware:Cookie/Yadro]
127.0.0.1  ad2.yam.com
127.0.0.1  ads.yam.com
127.0.0.1  bs.yandex.ru #[SecuritySpace.WebBug]
127.0.0.1  www.yandex.ru #[SunBelt.Yandex][Adware.SecureServicePk]
127.0.0.1  ybex.com
127.0.0.1  crsky2004.yeah.net #[Backdoor.Singu.B]
127.0.0.1  yeahsearch.info #[Spamdexing]
127.0.0.1  www.yeahsearch.info
127.0.0.1  www.yfdmedia.com
127.0.0.1  yiqilai.com #[Trojan.Yigather]
127.0.0.1  www.yogakorea.or.kr #[Win32/Spy.Banker.Big]
127.0.0.1  adplus.yonhapnews.co.kr
127.0.0.1  www.yop24.com #[MVPS.Criteria]
127.0.0.1  yourbestresult.com #[JS/Mht.O]
127.0.0.1  yourenhancement.com
127.0.0.1  www.yourenhancement.com #[eTrust.YourEnhancement][Trojan.Win32.VB.tg]
127.0.0.1  www.yourhitstats.com
127.0.0.1  ad.yourmedia.com
127.0.0.1  ad1.yourmedia.com
127.0.0.1  yournewindustry.net #[Javascript.Exploit]
127.0.0.1  www.yournewindustry.net
127.0.0.1  www.yourtracking.net
127.0.0.1  www.youshini.com #[Win32/PSW.Lineage.ACN]
127.0.0.1  yowoool.com #[Google.Warning]
127.0.0.1  ysearchus.com #[Parasite.TinyBar][SunBelt.TINYBAR]
127.0.0.1  www.ysearchus.com
127.0.0.1  www.y8ne.com #[Exploit.ANI]
127.0.0.1  www.yx2004.com #[AdWare.Win32.WinAD.ab]
127.0.0.1  www.yyc8.com #[Trojan.PWS.Wsgame][Exploit.ANI]
127.0.0.1  www.yykf.net #[VBS/TrojanDownloader.Agent.E]
127.0.0.1  www.yyue.com #[TROJ_STARTPAG.OC]
# [Z]
127.0.0.1  ad.zanox.com
127.0.0.1  zbox.zanox.com
127.0.0.1  zanox-affiliate.de
127.0.0.1  www.zanox-affiliate.de
127.0.0.1  www13.zapadserver1.com
127.0.0.1  www.zapadserver2.com
127.0.0.1  banners.zbs.ru
127.0.0.1  www.zcounter.com
127.0.0.1  zenux.info #[JS/Downloader-AUD]
127.0.0.1  www.zhangweijp.com #[Win32/PSW.Lineage.DN]
127.0.0.1  download.zhongsou.com #[Adware.SearchNet]
127.0.0.1  pig.zhongsou.com #[Adware-PigSearch]
127.0.0.1  zlalsky.com #[Google.Warning]
127.0.0.1  update.znew.org #[SpamBot]
127.0.0.1  counter.zone.ee
127.0.0.1  mp3.zonebg.com #[HJTH.C2Media/LOP variant]
127.0.0.1  zpsearch.com
127.0.0.1  www.zpsearch.com #[Backdoor.Win32.Delf.aki]
127.0.0.1  q.zpx520.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  bannerads.zwire.com
# [Misc]
127.0.0.1  banner.0catch.com
127.0.0.1  bannerimages.0catch.com #[dist.belnk.com]
127.0.0.1  tarjetas.0catch.com #[Win32/Small.JS]
127.0.0.1  s4.0stats.com
127.0.0.1  www.0stats.com
127.0.0.1  www.05168.com.tw #[VBS/TrojanDownloader.Agent.BA]
127.0.0.1  www.060s.com #[Win32/Prosti.C]
127.0.0.1  www.08325.cn #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.08cctv.com
127.0.0.1  union.0kis.com
127.0.0.1  banner.1and1.com
127.0.0.1  www.10s.com.br #[Trojan.Cargao]
127.0.0.1  www.104bay.com #[JS/Exploit.ADODB.Stream.NAG]
127.0.0.1  www.123gold.cn #[W32.Advegol]
127.0.0.1  123topsearch.com #[ADSPY/Agent.AP.7]
127.0.0.1  www.11468.com #[W32/Startpage.BZU]
127.0.0.1  www.1cyoga.com #[Google.Warning]
127.0.0.1  banner.1und1.com
127.0.0.1  banner.1and1.co.uk
127.0.0.1  123ads.nl
127.0.0.1  www.123hitcounter.com
127.0.0.1  123mania.com #[ADW_123MANIA.A]
127.0.0.1  www.123mania.com #[McAfee.Adware-123mania][Adware.MatrixSearch]
127.0.0.1  123stat.com
127.0.0.1  ad2.163.com
127.0.0.1  adclient.163.com
127.0.0.1  adgeo.163.com
127.0.0.1  1234.2bro.com #[Adware.Satbo]
127.0.0.1  ads.128b.com
127.0.0.1  18dmm.com #[Win32/TrojanDownloader.Delf.BHO]
127.0.0.1  bt.18dmm.com
127.0.0.1  www.18dmm.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.1800banners.com
127.0.0.1  www.1800freehits.com
127.0.0.1  www.1trac.com
127.0.0.1  count.2ch.net
127.0.0.1  www.20dy.cn #[NOD32.NewHeur_PE]
127.0.0.1  adserv.20six.net
127.0.0.1  ads.24.com
127.0.0.1  counter.24log.ru
127.0.0.1  www.241hits.com
127.0.0.1  counter.24log.com
127.0.0.1  tmp6.2ch.net #[Trojan.Sufiage]
127.0.0.1  2z0o.net #[Trojan.Popper]
127.0.0.1  pop1.2z0o.net #[admarketplace.net]
127.0.0.1  pop2.2z0o.net #[TROJ_DLOADER.AGS]
127.0.0.1  pop10.2z0o.net
127.0.0.1  req2.2z0o.net #[McAfee.Downloader-ACV]
127.0.0.1  181.365soft.info #[Win32/TrojanDownloader.Tiny.EU]
127.0.0.1  www.369.com #[Adware.LoadEWXD][McAfee.StartPage-JI]
127.0.0.1  www.3d-icons.com #[SiteAdvisor.3d-icons.com]
127.0.0.1  www.3deepspace.com #[SiteAdvisor.3deepspace.com]
127.0.0.1  www.3241.com #[Troj/Zikdow-B]
127.0.0.1  www.333sdesplaines.com #[Javascript.Exploit]
127.0.0.1  guannan.3322.net #[IE-SpyAd]
127.0.0.1  htmlcss.3322.org #[W32.Validin]
127.0.0.1  jietyu007.3322.org #[Trojan.Agentdoc.C]
127.0.0.1  localhosts.3322.org #[Win32/Ginwui]
127.0.0.1  love2046.3322.org #[Google.Warning]
127.0.0.1  rxjhgsta.3322.org #[Trojan.Agentdoc.B]
127.0.0.1  sina109.3322.org #[Win32/Hupigon]
127.0.0.1  download.35mb.com #[impregnable.net]
127.0.0.1  static.35mb.com #[HJTH.Win32.IstBar.fa]
127.0.0.1  www.35mb.com #[HJTH.MediaTickets Installer]
127.0.0.1  ad.37.com
127.0.0.1  404traff.com #[Spamdexing]
127.0.0.1  4affiliate.net
127.0.0.1  oasis.411affiliates.ca
127.0.0.1  adserver.4clicks.org
127.0.0.1  r.4at1.com
127.0.0.1  banners.4d5.net
127.0.0.1  4softget.com
127.0.0.1  ad.stat.4u.pl
127.0.0.1  adstat.4u.pl
127.0.0.1  www.40drinks.net #[Trojan-Spy.Win32.Banker.ark]
127.0.0.1  41m.com #[HJTH.XXXToolbar Variant][Trojan.Clicker.BL]
127.0.0.1  msncheck.41m.com
127.0.0.1  www.41m.com
127.0.0.1  www.4yousearch.com #[Spamdexing]
127.0.0.1  www.4061.it #[Win32/Haxdoor]
127.0.0.1  so.44986.com #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.453787.com #[Win32/PSW.Lineage.ACN]
127.0.0.1  www.475100.com #[Trojan.IEmax]
127.0.0.1  mm.47555.com
127.0.0.1  www.500sclintononline.com #[Javascript.Exploit]
127.0.0.1  softads.50webs.com
127.0.0.1  www.51.com #[Backdoor.CVM]
127.0.0.1  js.users.51.la
127.0.0.1  www.51liulan.cn #[Win32/Genetik]
127.0.0.1  count3.51yes.com
127.0.0.1  count5.51yes.com
127.0.0.1  count8.51yes.com
127.0.0.1  count9.51yes.com
127.0.0.1  count10.51yes.com
127.0.0.1  count12.51yes.com
127.0.0.1  count14.51yes.com
127.0.0.1  count15.51yes.com
127.0.0.1  count16.51yes.com
127.0.0.1  count17.51yes.com
127.0.0.1  count18.51yes.com
127.0.0.1  count19.51yes.com
127.0.0.1  count20.51yes.com
127.0.0.1  count24.51yes.com
127.0.0.1  count25.51yes.com
127.0.0.1  count28.51yes.com
127.0.0.1  count29.51yes.com
127.0.0.1  count30.51yes.com
127.0.0.1  count31.51yes.com
127.0.0.1  count32.51yes.com
127.0.0.1  count33.51yes.com
127.0.0.1  count35.51yes.com
127.0.0.1  count37.51yes.com
127.0.0.1  qq.520sf.org #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.54699.com #[Win32/Viking.AD]
127.0.0.1  www.555traff.net #[Javascript.Exploit]
127.0.0.1  www.555traff.org
127.0.0.1  a.56c.us #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  www.ff.iij4u.or.jp #[Trojan.Upchan]
127.0.0.1  ads.6arab.com
127.0.0.1  65552322.com
127.0.0.1  www.66ki.cn #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  ads.7days.ae
127.0.0.1  ad.71i.de
127.0.0.1  adserver.71i.de
127.0.0.1  7y7.us #[Win32/PSW.Delf.NHI]
127.0.0.1  7oo.meibu.com #[McAfee.BackDoor-CKB]
127.0.0.1  www.777seo.com #[Google.Warning]
127.0.0.1  www.7939.com #[TROJ_DELF.CNV]
127.0.0.1  mydown.79725.com #[McAfee.Downloader-AZN]
127.0.0.1  soswxyz.8800.org #[Trojan.Riler.F]
127.0.0.1  www.88889999.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  888-it.com #[AdWare.Win32.Casino.q]
127.0.0.1  www.888-it.com
127.0.0.1  ajim.delphibbs.com #[Trojan.PSW.Ajim_bbs]
127.0.0.1  pp.900666.com #[HTML/Exploit.Ascii.NAA]
127.0.0.1  www.911traff.com #[Javascript.Exploit]
127.0.0.1  www.9991.com #[Backdoor.CVM][Adware.PPRich]
127.0.0.1  www.999x.com #[Backdoor.CVM]
127.0.0.1  www.9ringtone.com
127.0.0.1  www.18hi.net #[McAfee.StartPage-HR]
127.0.0.1  www.19ku.com #[McAfee.StartPage-HR]
127.0.0.1  10000hits.net #[SunBelt.Cookie.10000hits]
# [123Banners][123Greetings.com][TROJ_NALDEM.A][Trojan.Naldem]
127.0.0.1  www.123banners.com
127.0.0.1  ftp.123banners.com
127.0.0.1  123go.com
127.0.0.1  ns1.123go.net
# [180Solutions][CDT Inc][Zango Canada]
127.0.0.1  180solutions.com
127.0.0.1  ads.180solutions.com
127.0.0.1  ax.180solutions.com
127.0.0.1  bis.180solutions.com #[ADW_SOLU180.F]
127.0.0.1  config.180solutions.com #[eTrust.180SearchAssistant]
127.0.0.1  cts.180solutions.com
127.0.0.1  downloads.180solutions.com #[McAfee.Adware-ZangoSA.dldr][server down?]
127.0.0.1  his.180solutions.com
127.0.0.1  installs.180solutions.com #[server down?]
127.0.0.1  ping.180solutions.com
127.0.0.1  tv.180solutions.com
127.0.0.1  tvf.180solutions.com
127.0.0.1  www.180solutions.com
127.0.0.1  www.180solutions.net
127.0.0.1  infinity.180searchassistant.com #[ADW_SOLU180.H]
127.0.0.1  msxml.180searchassistant.com #[msxml.infospace.com]
127.0.0.1  powered-by.180searchassistant.com
127.0.0.1  searchresults.180searchassistant.com
127.0.0.1  www.180searchassistant.com #[Adware.180Search]
127.0.0.1  www.abcfreedownloads.com
127.0.0.1  www.abcfreegames.com
127.0.0.1  freegamesclub.com
127.0.0.1  www.fullarmorstudios.com
127.0.0.1  www.games4good.net
127.0.0.1  content.licenseacquisition.org #[Troj/QLowZon-EV]
127.0.0.1  drm.licenseacquisition.org
127.0.0.1  media.licenseacquisition.org #[SiteAdvisor.licenseacquisition.org]
127.0.0.1  origin-cached.licenseacquisition.org
127.0.0.1  preview.licenseacquisition.org
127.0.0.1  loudcash.com
127.0.0.1  partners.loudcash.com
127.0.0.1  www.loudcash.com
127.0.0.1  metricsdirect.com
127.0.0.1  ads.metricsdirect.com
127.0.0.1  cts.metricsdirect.com
127.0.0.1  reports.metricsdirect.com
127.0.0.1  www.metricsdirect.com
127.0.0.1  www.myfreegamedownloads.com
127.0.0.1  n-case.com
127.0.0.1  www.n-case.com #[Panda.Adware/nCase]
127.0.0.1  page-not-found.org
127.0.0.1  search.prositefinder.com #[SunBelt.bho.180Solutions.ProSiteFinder]
127.0.0.1  seekmo.com #[Adware.180Solutions.SearchAssistant]
127.0.0.1  config.seekmo.com
127.0.0.1  cts.seekmo.com
127.0.0.1  downloads.seekmo.com
127.0.0.1  installs.seekmo.com
127.0.0.1  powered-by.seekmo.com
127.0.0.1  tvf.seekmo.com
127.0.0.1  allofthevideos.powered-by.seekmo.com
127.0.0.1  freeblowjobmovies.powered-by.seekmo.com
127.0.0.1  freeblowjobvideos.powered-by.seekmo.com
127.0.0.1  funberry.powered-by.seekmo.com
127.0.0.1  keyrastriptease.powered-by.seekmo.com
127.0.0.1  male-celeb-videos.powered-by.seekmo.com
127.0.0.1  pariswallpapers.powered-by.seekmo.com #[WildcardDNS]
127.0.0.1  slutmatrixfree.powered-by.seekmo.com
127.0.0.1  vidshrine.com.powered-by.seekmo.com
127.0.0.1  wallpapernudes.powered-by.seekmo.com
127.0.0.1  tv.seekmo.com #[MVPS.Criteria]
127.0.0.1  www.seekmo.com
127.0.0.1  tons-of-free-downloads.com
127.0.0.1  tons-of-free-games.com
127.0.0.1  www.tonsoffreedownloads.com
127.0.0.1  www.tonsoffreegames.com
127.0.0.1  www.totallycoolfreedownloads.com
127.0.0.1  www.totallyfreeadultstuff.com
127.0.0.1  www.totallyfreeadultvideos.com
127.0.0.1  totallyfunfreegames.com
127.0.0.1  www.totallyfunfreegames.com
127.0.0.1  white.totallyfunfreestuff.com
127.0.0.1  www.totallyfunfreestuff.com
127.0.0.1  winadclient.com
127.0.0.1  eula.winadclient.com
127.0.0.1  www.winadclient.com
127.0.0.1  windupdates.com #[Adware.WinTaskAd][Trojan.TrustedZones]
127.0.0.1  public.windupdates.com #[Windows SyncroAd]
127.0.0.1  static.windupdates.com #[ADW_WUPD.F][ADW_WINSTATX.A]
127.0.0.1  www.windupdates.com #[AdvWare.WinAD][ADSPY/WiAD.AF.1]
127.0.0.1  zango.com #[SiteAdvisor.zango]
127.0.0.1  adservices.zango.com
127.0.0.1  analytics.zango.com #[zango.com.112.2o7.net]
127.0.0.1  cds.zango.com
127.0.0.1  acces.powered-by.zango.com
127.0.0.1  animeim.powered-by.zango.com
127.0.0.1  annakournikova.powered-by.zango.com
127.0.0.1  clickpixcursors.powered-by.zango.com
127.0.0.1  coolvuurwerk.powered-by.zango.com
127.0.0.1  dane-cook.powered-by.zango.com
127.0.0.1  davesemu.com.powered-by.zango.com
127.0.0.1  deansplanet.com.powered-by.zango.com #[WildcardDNS]
127.0.0.1  factorygames.powered-by.zango.com
127.0.0.1  fightvideos.powered-by.zango.com
127.0.0.1  fightvids.powered-by.zango.com
127.0.0.1  flashaddictinggames.powered-by.zango.com
127.0.0.1  frazoogames.powered-by.zango.com
127.0.0.1  free.karaoke.songs.powered-by.zango.com
127.0.0.1  freesudokus.powered-by.zango.com
127.0.0.1  freetoplay.ath.cx.powered-by.zango.com
127.0.0.1  games.byethost32.powered-by.zango.com
127.0.0.1  gate1.powered-by.zango.com
127.0.0.1  gate2.powered-by.zango.com
127.0.0.1  gate3.powered-by.zango.com
127.0.0.1  gate4.powered-by.zango.com
127.0.0.1  gate5.powered-by.zango.com
127.0.0.1  gate6.powered-by.zango.com
127.0.0.1  gate7.powered-by.zango.com
127.0.0.1  gate8.powered-by.zango.com
127.0.0.1  gate9.powered-by.zango.com
127.0.0.1  gate10.powered-by.zango.com
127.0.0.1  gate11.powered-by.zango.com
127.0.0.1  gate12.powered-by.zango.com
127.0.0.1  gauntletvideos.powered-by.zango.com
127.0.0.1  getmusicvideocodes.powered-by.zango.com
127.0.0.1  graffitifonts.powered-by.zango.com #[Wildcard DNS]
127.0.0.1  hot-lindsay.powered-by.zango.com
127.0.0.1  iconcave.powered-by.zango.com
127.0.0.1  idrink.powered-by.zango.com
127.0.0.1  lavacards.powered-by.zango.com
127.0.0.1  martinahingis.powered-by.zango.com
127.0.0.1  maratsafin.powered-by.zango.com
127.0.0.1  mediagecko.powered-by.zango.com
127.0.0.1  midis.powered-by.zango.com
127.0.0.1  mmocenter.org.powered-by.zango.com
127.0.0.1  musicvideocodes.powered-by.zango.com
127.0.0.1  mvcodezone.powered-by.zango.com
127.0.0.1  mydisplayimage.powered-by.zango.com
127.0.0.1  myfriendspy.powered-by.zango.com
127.0.0.1  mymoneymakers.powered-by.zango.com
127.0.0.1  myspace.powered-by.zango.com
127.0.0.1  myspace-backgrounds.powered-by.zango.com
127.0.0.1  myspace-codes.powered-by.zango.com
127.0.0.1  myspacegraphics.powered-by.zango.com
127.0.0.1  myspacegraphicsx.powered-by.zango.com
127.0.0.1  myspaceicons.powered-by.zango.com
127.0.0.1  myspaceiconsorg.powered-by.zango.com
127.0.0.1  myspacelayouts.powered-by.zango.com
127.0.0.1  mytop12.com.powered-by.zango.com
127.0.0.1  narutowallpaper.powered-by.zango.com
127.0.0.1  newgrounds.dressup.powered-by.zango.com
127.0.0.1  pbxanime.powered-by.zango.com
127.0.0.1  people2people.powered-by.zango.com
127.0.0.1  phoenixpeople.powered-by.zango.com
127.0.0.1  planet.nana.co.il.powered-by.zango.com
127.0.0.1  pokemonporn.powered-by.zango.com
127.0.0.1  screensaverparadise.powered-by.zango.com
127.0.0.1  sfondigratis.powered-by.zango.com
127.0.0.1  stacy-keibler-pictures.powered-by.zango.com
127.0.0.1  snapshot.powered-by.zango.com
127.0.0.1  theamazingracist.powered-by.zango.com
127.0.0.1  trenchracing.powered-by.zango.com
127.0.0.1  vcc.powered-by.zango.com
127.0.0.1  vimalonline.powered-by.zango.com
127.0.0.1  videocodesworld.powered-by.zango.com
127.0.0.1  whatsthatcode.com.powered-by.zango.com
127.0.0.1  wwedivas.powered-by.zango.com
127.0.0.1  xtreme-cheats.powered-by.zango.com
127.0.0.1  downloads.zango.com #[SunBelt.180Solutions.Zango.TVTimes]
127.0.0.1  games.zango.com #[SunBelt.Adw.Zango.Solitaire]
127.0.0.1  imp.games.zango.com
127.0.0.1  lp.zango.com #[McAfee.Adware-ZangoSA]
127.0.0.1  messenger.zango.com
127.0.0.1  msxml.zango.com #[msxml.infospace.com]
127.0.0.1  partner.zango.com
127.0.0.1  powered-by.zango.com
127.0.0.1  shared.zango.com
127.0.0.1  showtimes.zango.com #[SpySweeper.180search assistant/zango]
127.0.0.1  sitefinder.zango.com #[zangositefinder.simpli.com][ValueClick]
127.0.0.1  tv.zango.com
127.0.0.1  www.zango.com #[Adware.ZangoSearch]
127.0.0.1  zangocash.com #[SiteAdvisor.zangocash.com]
127.0.0.1  partner.zangocash.com
127.0.0.1  prompt.zangocash.com #[eTrust.Win32/Anyhomb.D]
127.0.0.1  public.zangocash.com
127.0.0.1  static.zangocash.com #[CVE-2006-2324][Troj/QLowZon-EV]
127.0.0.1  syndication.zangocash.com
127.0.0.1  www.zangocash.com
127.0.0.1  www.zangogames.com
127.0.0.1  www.zangomessenger.com
127.0.0.1  www.zangopartner.com
127.0.0.1  www.zangopartner.net
# [2KDirect]
127.0.0.1  www.gms1.net #[McAfee.Adware-IEHost]
127.0.0.1  geo.precisionclick.com
127.0.0.1  servedby.precisionclick.com
# [3721.COM][Yahoo]
127.0.0.1  cnsmin.3721.com
127.0.0.1  download.3721.com #[McAfee.Adware-BDSearch]
127.0.0.1  www.3721.com #[Adware.Chinet][ADW_CNSMIN.A]
127.0.0.1  count.3721.yahoo.com
# [411 Web Directory]
127.0.0.1  ad.411web.com
127.0.0.1  adtracker.411web.com
127.0.0.1  hits.411web.com
127.0.0.1  search.411web.com
127.0.0.1  static.411web.com
127.0.0.1  xml.411web.com
127.0.0.1  www.411web.com
127.0.0.1  search.letssearch.com
127.0.0.1  www.letssearch.com #[BrowserAid.LetsSearch]
# [7Search.com Networks][EMERgency 24, Inc]
127.0.0.1  7search.com #[Adware.7FaSSt]
127.0.0.1  fstrack.7search.com
127.0.0.1  ia1.7search.com
127.0.0.1  img.7search.com
127.0.0.1  meta.7search.com
127.0.0.1  impression.7search.com
127.0.0.1  www.7search.com #[Spyware.SevenSearch]
127.0.0.1  77search.com
127.0.0.1  img.7meta.com
127.0.0.1  www.7metasearch.com
127.0.0.1  www.a1fax.com
127.0.0.1  adtactics.com
127.0.0.1  bannerx.adtactics.com
127.0.0.1  www.adtactics.com
127.0.0.1  advertisingagent.com
127.0.0.1  ajokeaday.com
127.0.0.1  bannersxchange.com
127.0.0.1  img.bannersxchange.com
127.0.0.1  www.bannersxchange.com
127.0.0.1  bestsearch.com
127.0.0.1  scripts.bestsearch.com
127.0.0.1  www.bestsearch.com
127.0.0.1  browseraccelerator.com #[Spyware.BrowserAccel]
127.0.0.1  data.browseraccelerator.com
127.0.0.1  download.browseraccelerator.com
127.0.0.1  client.browseraccelerator.com
127.0.0.1  www.browseraccelerator.com
127.0.0.1  www.buscamundo.com
127.0.0.1  internetsecurity.com
127.0.0.1  www.internetsecurity.com
127.0.0.1  www.payperranking.com
127.0.0.1  www.pay-per-search.com
127.0.0.1  paypertext.com
127.0.0.1  predictivesearch.com
127.0.0.1  seal.ranking.com
127.0.0.1  www.ranking.com
127.0.0.1  tracking.roispy.com
127.0.0.1  www.roispy.com #[SunBelt.ROISpy.com]
127.0.0.1  ftp.sevenmetasearch.com
127.0.0.1  www.sevenmetasearch.com
127.0.0.1  tracking.spiderbait.com
127.0.0.1  www.spiderbait.com
127.0.0.1  www.textadvertising.com
127.0.0.1  www.thetop10.com
127.0.0.1  trustgauge.com
127.0.0.1  www.trustgauge.com
127.0.0.1  seal.validatedsite.com
127.0.0.1  www.validatedsite.com
127.0.0.1  www.watch24.com
# [About.com]
127.0.0.1  clicks.about.com
127.0.0.1  f.about.com
127.0.0.1  home.about.com
127.0.0.1  images.about.com
127.0.0.1  lunafetch.about.com
127.0.0.1  pixel3.about.com
127.0.0.1  sprinks-clicks.about.com
127.0.0.1  statistics.s5.com
127.0.0.1  ad.aboutwebservices.com
# [AboveNet Communications]
127.0.0.1  btn.clickability.com
127.0.0.1  button.clickability.com #[Wildcard DNS]
127.0.0.1  cas.clickability.com
127.0.0.1  imp.clickability.com
127.0.0.1  ri.clickability.com #[SunBelt.Clickability.com]
127.0.0.1  s.clickability.com
127.0.0.1  sftp.clickability.com #[Tenebril.Tracking.Cookie]
127.0.0.1  stats.clickability.com #[eTrust.Tracking.Cookie]
# [Accipiter Solutions]
127.0.0.1  ad101com.adbureau.net #[a900.g.akamai.net]
127.0.0.1  ad101com-images.adbureau.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  admse001.adbureau.net
127.0.0.1  admse001-images.adbureau.net
127.0.0.1  adops.adbureau.net
127.0.0.1  capitali-images.adbureau.net #[a900.g.akamai.net]
127.0.0.1  cent.adbureau.net
127.0.0.1  creview.adbureau.net
127.0.0.1  creview-images.adbureau.net #[a900.g.akamai.net]
127.0.0.1  cvapts-images.adbureau.net
127.0.0.1  devart.adbureau.net
127.0.0.1  divx.adbureau.net
127.0.0.1  dnsstuff.adbureau.net
127.0.0.1  eb.adbureau.net
127.0.0.1  granada.adbureau.net
127.0.0.1  granada-images.adbureau.net
127.0.0.1  haynet-images.adbureau.net
127.0.0.1  hbpl-images.adbureau.net
127.0.0.1  ieee.adbureau.net
127.0.0.1  ieee-images.adbureau.net
127.0.0.1  imediac.adbureau.net
127.0.0.1  inl.adbureau.net
127.0.0.1  katu.adbureau.net
127.0.0.1  mediapst.adbureau.net
127.0.0.1  metro-images.adbureau.net
127.0.0.1  metro.adbureau.net
127.0.0.1  ozone-images.adbureau.net
127.0.0.1  pntm.adbureau.net
127.0.0.1  questex-images.adbureau.net
127.0.0.1  sixapart.adbureau.net
127.0.0.1  splendid.adbureau.net
127.0.0.1  sportsad.adbureau.net
127.0.0.1  studenti.adbureau.net
127.0.0.1  tripadv-images.adbureau.net
127.0.0.1  videoegg.adbureau.net
127.0.0.1  vmix.adbureau.net
127.0.0.1  vpoint-images.adbureau.net
127.0.0.1  www.adbureau.net
127.0.0.1  venture.boulevards.com #[metro.adbureau.net]
127.0.0.1  display.hbpl.co.uk #[hbpl.adbureau.net]
127.0.0.1  inv.questex.com #[questex.adbureau.net]
# [Accoona Corp]
127.0.0.1  www.accoona.cn
127.0.0.1  search.accoona.com
127.0.0.1  www.accoona.com #[Adware-Accoona][Adware.Atoolb][Panda.Accoona]
127.0.0.1  www.accoonachess.com
# [Acez Software][Adware-NuggetSearch.dr]
127.0.0.1  s1.acez.com
127.0.0.1  www.acez.com #[AdWare.BHO.MegaSearch.b][SiteAdvisor.acez.com]
127.0.0.1  www.acezsoftware.com
127.0.0.1  www.searchnugget.com #[Adware.SearchNugget]
127.0.0.1  www.screengizmos.com
127.0.0.1  www.siteerror.com #[siteError.dll]
# [AdBrite, Inc]
127.0.0.1  adbrite.com #[Ewido.TrackingCookie.Adbrite]
127.0.0.1  1.adbrite.com
127.0.0.1  2.adbrite.com #[SiteAdvisor.findwhatevernow.com]
127.0.0.1  3.adbrite.com
127.0.0.1  4.adbrite.com
127.0.0.1  ads.adbrite.com
127.0.0.1  click.adbrite.com
127.0.0.1  files.adbrite.com
127.0.0.1  pic.adbrite.com
127.0.0.1  vid.adbrite.com
127.0.0.1  site.www.adbrite.com
127.0.0.1  stats.adbrite.com
127.0.0.1  www.adbrite.com
127.0.0.1  www.avnads.com
127.0.0.1  www.britepic.com
127.0.0.1  1.httpads.com #[1adbrite.adbrite.com.akadns.net]
127.0.0.1  1.marketbanker.com
127.0.0.1  2.marketbanker.com
127.0.0.1  www.marketbanker.com
# [Adknowledge]
127.0.0.1  adsvr.adknowledge.com
127.0.0.1  bidsystem.adknowledge.com
127.0.0.1  bsclick.adknowledge.com
127.0.0.1  web.adknowledge.com #[McAfee.Cookie-Adknowledge]
127.0.0.1  ak1.cc
127.0.0.1  dyn.ak1.cc
127.0.0.1  app.desktop.ak-networks.com #[aklsp.dll][TrojanDownloader.Win32.Agent.br]
127.0.0.1  updates.desktop.ak-networks.com
127.0.0.1  vlogic.ak-networks.com #[lspak.dll]
# [AdOrigin Corp]
127.0.0.1  ads.adorigin.com #[SpySweeper.Spy.Cookie]
127.0.0.1  dev.adorigin.com
127.0.0.1  servedby.adorigin.com
127.0.0.1  www.adorigin.com #[Ewido.TrackingCookie.Adorigin]
127.0.0.1  blowsearch.com #[SunBelt.BlowSearch.com]
127.0.0.1  msxml.blowsearch.com
127.0.0.1  web.blowsearch.com #[infospace.com]
127.0.0.1  www.blowsearch.com #[Tenebril.Tracking.Cookie]
# [ADSoft][Hot Lab][ADSoft-Development]
127.0.0.1  www.1-viagra-on-line.com
127.0.0.1  www.all-casinos.org
127.0.0.1  www.all-lyrics.org
127.0.0.1  www.best-poker.biz
127.0.0.1  www.chenjesu.com
127.0.0.1  halflemon.com #[Adware.HalfLemon][Trojan.Win32.StartPage.ya]
127.0.0.1  www.halflemon.com
127.0.0.1  www.spycounter.net
127.0.0.1  www-start-page.com #[Adware.HalfLemon]
127.0.0.1  www.www-start-page.com #[Trojan.Win32.StartPage.ya]
127.0.0.1  www.start-page.net
127.0.0.1  www.start-page.org
127.0.0.1  the-roulette.net
127.0.0.1  www.usa-phendimetrazine.com
127.0.0.1  www.x-stats.info #[Spamdexing]
# [Ad-Souk AdServer]
127.0.0.1  www.ad-souk.com
127.0.0.1  bilbob.com
127.0.0.1  didtal.com
127.0.0.1  quinst.com
# [Adteractive]
127.0.0.1  cb.adprofile.net
127.0.0.1  content.adprofile.net
127.0.0.1  tx.adprofile.net
127.0.0.1  w2-ver.adprofile.net #[SpySweeper.Spy.Cookie]
127.0.0.1  adteractive.com
127.0.0.1  www.adteractive.com
127.0.0.1  icc.intellisrv.net
# [Adtegrity.com, Inc]
127.0.0.1  adtegrity.com
127.0.0.1  www.adtegrity.com
127.0.0.1  webalize.com #[SearchCentrix][VisiCom.SearchCentric]
127.0.0.1  www.webalize.com #[Visicom Media Toolbar]
127.0.0.1  webalize.net
127.0.0.1  www.webalize.net
127.0.0.1  webalize.mygeek.com
# [Adtomi]
127.0.0.1  adtomi.com
127.0.0.1  ads.adtomi.com #[ADW_ADTOMI.D]
127.0.0.1  www.adtomi.com #[Adware.Adtomi]
# [AdvertPro][Renegade Internet]
127.0.0.1  800comm.advertserve.com
127.0.0.1  aalbc.advertserve.com
127.0.0.1  adpowerzone.advertserve.com #[Whios.Blacklisted]
127.0.0.1  bayoubuzz.advertserve.com
127.0.0.1  candlefind.advertserve.com
127.0.0.1  circuit.advertserve.com
127.0.0.1  d2.advertserve.com
127.0.0.1  divavillage.advertserve.com
127.0.0.1  ecnext.advertserve.com
127.0.0.1  endi.advertserve.com
127.0.0.1  finalternatives.advertserve.com
127.0.0.1  financialcontent.advertserve.com
127.0.0.1  findbliss.advertserve.com
127.0.0.1  fishandfly.advertserve.com
127.0.0.1  fx-charts.advertserve.com
127.0.0.1  gazetteextra.advertserve.com
127.0.0.1  glide.advertserve.com
127.0.0.1  himss.advertserve.com
127.0.0.1  ipt.advertserve.com
127.0.0.1  ipt-ltd.advertserve.com
127.0.0.1  iresources.advertserve.com
127.0.0.1  lan.advertserve.com
127.0.0.1  medbanner.advertserve.com
127.0.0.1  monstersandcritics.advertserve.com
127.0.0.1  musictowers.advertserve.com
127.0.0.1  observer.advertserve.com
127.0.0.1  oppknocks.advertserve.com
127.0.0.1  projectorreviews.advertserve.com
127.0.0.1  smartcpc.advertserve.com
127.0.0.1  switzerland.advertserve.com
127.0.0.1  topica.advertserve.com
127.0.0.1  tradearabia.advertserve.com
127.0.0.1  trucking.advertserve.com
127.0.0.1  unleash.advertserve.com
127.0.0.1  www.advertserve.com
# [Alex Walter][Spectre][4F8 Networks][Xyfex]
127.0.0.1  install.007guard.com
127.0.0.1  download.007guard.com
127.0.0.1  the.007guard.com
127.0.0.1  www.007guard.com #[SiteAdvisor.007guard.com]
127.0.0.1  2search.org #[Adware.2Search][eTrust.2Search]
127.0.0.1  feeds.2search.org
127.0.0.1  feeds2.2search.org #[McAfee.Adware-2Search.dr]
127.0.0.1  www.2search.org #[clickheretofind.com]
127.0.0.1  bardownload.com
127.0.0.1  download.bardownload.com
127.0.0.1  www.bardownload.com #[MHTMLRedir.Exploit][SiteAdvisor.bardownload.com]
127.0.0.1  hotmsnnames.com #[Adware bundler]
127.0.0.1  emoticons.hotmsnnames.com
127.0.0.1  www.hotmsnnames.com
127.0.0.1  www.hottestgames.net
127.0.0.1  www.im-names.com #[Adware.IMNames]
127.0.0.1  www.msgr-names.com #[Win32/Adware.2Search]
127.0.0.1  adserver.shizzlehost.com
127.0.0.1  domains.shizzlehost.com
127.0.0.1  www.shizzlelyrics.com
127.0.0.1  www.shizzletraffic.com
127.0.0.1  www.xyfex.com
# [AlmondNet Ltd Group][Zeno Tecnico S.A][Think-Adz]
127.0.0.1  getsudoku4free.com #[AdWare.Win32.ZenoSearch.d]
127.0.0.1  www.getsudoku4free.com
127.0.0.1  ads.pro-market.net #[SpySweeper.Spy.Cookie][a1947.x.akamai.net]
127.0.0.1  pbid.pro-market.net
127.0.0.1  www.think-adz2.com
127.0.0.1  www.zenotecnico2.com
# [Asher Nahmias]
127.0.0.1  i--search.com #[SunBelt.SearchUpgrade]
127.0.0.1  www.i--search.com #[StartPage-FN]
127.0.0.1  zeropopup.com #[Parasite.ZeroPopUp]
127.0.0.1  www.zeropopup.com #[Tellafriend.Trojan]
# [AD TECH AG][Adtech.de]
127.0.0.1  adtech.de #[Ad-Aware.Tracking.Cookie]
127.0.0.1  adforce.adtech.de
127.0.0.1  adserver.adtech.de #[ADTECH Group JavaScript TAG]
127.0.0.1  ad.dc2.adtech.de
127.0.0.1  im.adtech.de
127.0.0.1  imageserv.adtech.de
127.0.0.1  img-pcdn.adtech.de #[g1.panthercdn.com]
127.0.0.1  livingnet.adtech.de #[McAfee.Cookie-Adtech]
127.0.0.1  x86adserv001.adtech.de
127.0.0.1  x86adserv002.adtech.de
127.0.0.1  x86adserv003.adtech.de #[SunBelt.Adtech.de]
127.0.0.1  x86adserv004.adtech.de
127.0.0.1  x86adserv005.adtech.de
127.0.0.1  x86adserv006.adtech.de
127.0.0.1  x86adserv007.adtech.de #[Kephyr.PUP]
127.0.0.1  x86adserv008.adtech.de
127.0.0.1  x86adserv009.adtech.de
127.0.0.1  x86adserv010.adtech.de
127.0.0.1  x86adserv011.adtech.de #[MVPS.Criteria]
127.0.0.1  x86adserv012.adtech.de
127.0.0.1  x86adserv013.adtech.de
127.0.0.1  x86adserv014.adtech.de
127.0.0.1  x86adserv015.adtech.de #[Ewido.Spyware.Cookie.Adtech]
127.0.0.1  x86adserv016.adtech.de
127.0.0.1  x86adserv017.adtech.de
127.0.0.1  x86adserv018.adtech.de
127.0.0.1  adserver.adremedy.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  adserver.easyad.info
# [Advertising.com][AOL]
127.0.0.1  cdn1.adsdk.com
127.0.0.1  cdn2.adsdk.com #[a1906.g.akamai.net][VirtualBouncer]
127.0.0.1  advertising.com
127.0.0.1  ace-lb.advertising.com
127.0.0.1  adserve.advertising.com
127.0.0.1  bannerfarm.ace.advertising.com #[Tenebril.Tracking.Cookie]
127.0.0.1  dbs.advertising.com
127.0.0.1  demo.advertising.com
127.0.0.1  leadback.advertising.com #[adv.service.mirror-image.net]
127.0.0.1  opera1-servedby.advertising.com
127.0.0.1  secure.leadback.advertising.com #[adv.service.mirror-image.net]
127.0.0.1  servedby.advertising.com #[eTrust.Tracking.Cookie]
127.0.0.1  rd.advertising.com
127.0.0.1  wap.advertising.com
127.0.0.1  www.advertising.com #[Ewido.Spyware.Cookie.Advertising]
127.0.0.1  clk4.com
127.0.0.1  dev.clk4.com
127.0.0.1  www.clk4.com
127.0.0.1  www.contextualclicks.com
127.0.0.1  fastseeker.com #[Adware.FastSeek]
127.0.0.1  www.fastseeker.com
127.0.0.1  bf.mocda1.com
127.0.0.1  spyblast.com #[SiteAdvisor.spyblast.com]
127.0.0.1  www.spyblast.com #[Rogue/Suspect]
127.0.0.1  www.thesearchster.com
# [Aleksej Novikov]
127.0.0.1  rotor6.newzfind.com
127.0.0.1  sutra.newzfind.com
# [Alex Korsakoff]
127.0.0.1  7art-screensavers.com #[Trojan-Downloader.Win32.PurityScan.eg]
127.0.0.1  flowers.7art-screensavers.com
127.0.0.1  www.7art-screensavers.com
127.0.0.1  silveragesoftware.com #[SiteAdvisor.silveragesoftware.com]
127.0.0.1  www.silveragesoftware.com
# [Alexej Rostaslavovitch]
127.0.0.1  www.crazygirls-world.com #[the-best-promos.com]
127.0.0.1  www.gad-network.com
127.0.0.1  www.games-desktop.com #[akamai.downloadv3.com]
127.0.0.1  www.go-astro.com #[Backdoor.Win32.Iroffer.Z]
127.0.0.1  www.go-turf.com
127.0.0.1  www.gomusic.com
127.0.0.1  www.gorecord.com
127.0.0.1  www.hot-tv.com #[Win32/Skintrim!]
127.0.0.1  www.internetgamebox.com #[Backdoor.Win32.Iroffer.Z]
127.0.0.1  www.lastsoftwares.com #[zipzappromos.com]
127.0.0.1  www.mail-skinner.com #[server down?]
127.0.0.1  www.mailskinner.com #[Backdoor.Win32.Iroffer.Z][Trojan.Skintrim]
127.0.0.1  www.navi-recherche.com
127.0.0.1  www.navi-search.com
127.0.0.1  www.serialplayers.com #[the-best-promos.com]
127.0.0.1  www.sudoplanet.com #[Win32/Skintrim!]
127.0.0.1  www.web-mediaplayer.com #[Backdoor.Win32.Iroffer.Z]
127.0.0.1  www.videozapping.com
# [Altnet][Adware.BDE][Adware.Topsearch.B]
127.0.0.1  altnet.com
127.0.0.1  file.altnet.com
127.0.0.1  media.altnet.com
127.0.0.1  ts.altnet.com
127.0.0.1  tss.altnet.com
127.0.0.1  pm.altnet.com
127.0.0.1  www.altnet.com #[ADW_ALTNET.A]
127.0.0.1  www.altnetp2p.com
127.0.0.1  brilliantdigital.com #[Parasite.BDE]
127.0.0.1  st.brilliantdigital.com
127.0.0.1  www.brilliantdigital.com #[TROJ_KREPPER.Y]
127.0.0.1  b3d.com
127.0.0.1  bde3d.com
127.0.0.1  www.b3d.com
# [Andreas Pizsa]
127.0.0.1  www.behind-firewall.com #[AdWare.Win32.WebHancer.320]
127.0.0.1  www.firewall-tunnel.com
127.0.0.1  www.free-proxy.org
127.0.0.1  www.get-around-firwall.com
127.0.0.1  www.hide-ip.com
127.0.0.1  www.hopster.com #[AdWare.Win32.WebHancer.320]
127.0.0.1  www.http-proxy.com
127.0.0.1  www.http-tunnel.org
127.0.0.1  www.http-tunnel.net
127.0.0.1  www.http-tunneling.com
127.0.0.1  www.irc-proxy.com
127.0.0.1  www.kazaa-firewall.com
127.0.0.1  www.kazaa-proxy.com
127.0.0.1  www.kill-firewall.com
127.0.0.1  www.msn-firewall.com
127.0.0.1  www.msn-proxy.com
127.0.0.1  www.proxy-bypass.com
127.0.0.1  www.proxy-tunnel.com
127.0.0.1  www.socks-proxy.org
# [Applied Technologies Internet][Tracking Service]
127.0.0.1  hit-parade.com
127.0.0.1  loga.hit-parade.com
127.0.0.1  logp.hit-parade.com
127.0.0.1  xiti.com
127.0.0.1  loga.xiti.com #[SpySweeper.Spy.Cookie]
127.0.0.1  logc2.xiti.com
127.0.0.1  logc7.xiti.com
127.0.0.1  logc8.xiti.com
127.0.0.1  logc13.xiti.com
127.0.0.1  logc14.xiti.com
127.0.0.1  logc15.xiti.com
127.0.0.1  logc16.xiti.com
127.0.0.1  logc19.xiti.com
127.0.0.1  logc25.xiti.com #[crossdomain.xml]
127.0.0.1  logc31.xiti.com
127.0.0.1  logi6.xiti.com
127.0.0.1  logi7.xiti.com
127.0.0.1  logi8.xiti.com
127.0.0.1  logi9.xiti.com
127.0.0.1  logi10.xiti.com
127.0.0.1  logi11.xiti.com
127.0.0.1  logi12.xiti.com
127.0.0.1  logp.xiti.com
127.0.0.1  logp3.xiti.com
127.0.0.1  logv1.xiti.com
127.0.0.1  logv2.xiti.com
127.0.0.1  logv3.xiti.com #[Panda.Spyware:Cookie/Xiti]
127.0.0.1  logv4.xiti.com
127.0.0.1  logv5.xiti.com
127.0.0.1  logv6.xiti.com
127.0.0.1  logv7.xiti.com
127.0.0.1  logv8.xiti.com
127.0.0.1  logv9.xiti.com
127.0.0.1  logv10.xiti.com
127.0.0.1  logv11.xiti.com
127.0.0.1  logv12.xiti.com
127.0.0.1  logv13.xiti.com
127.0.0.1  logv14.xiti.com
127.0.0.1  logv15.xiti.com
127.0.0.1  logv16.xiti.com
127.0.0.1  logv17.xiti.com
127.0.0.1  logv18.xiti.com #[SecuritySpace.web bug]
127.0.0.1  logv19.xiti.com
127.0.0.1  logv20.xiti.com
127.0.0.1  logv21.xiti.com
127.0.0.1  logv22.xiti.com
127.0.0.1  logv23.xiti.com
127.0.0.1  logv24.xiti.com
127.0.0.1  logv25.xiti.com
127.0.0.1  logv26.xiti.com
127.0.0.1  logv27.xiti.com
127.0.0.1  logv28.xiti.com
127.0.0.1  logv29.xiti.com
127.0.0.1  logv30.xiti.com
127.0.0.1  logv31.xiti.com
127.0.0.1  logv32.xiti.com
127.0.0.1  trafic.xiti.com
127.0.0.1  www.xiti.com
# [aQuantive Inc][Microsoft]
127.0.0.1  www.avenuea.com
127.0.0.1  click.atdmt.com #[McAfee.Cookie-Atdmt]
# 127.0.0.1  clk.atdmt.com #[disabled affects MS downloads]
127.0.0.1  image.atdmt.com
127.0.0.1  mir.atdmt.com #[p.mii.instacontent.net]
127.0.0.1  nc.atdmt.com #[EventTracking]
127.0.0.1  rmd.atdmt.com #[a898.x.akamai.net]
127.0.0.1  spd.atdmt.com #[a796.x.akamai.net]
127.0.0.1  spe.atdmt.com
127.0.0.1  srch.atdmt.com
# 127.0.0.1  switch.atdmt.com #[disabled affects Hotmail signup]
127.0.0.1  view.atdmt.com #[eTrust.Tracking.Cookie]
127.0.0.1  www.atdmt.com #[AveA Action Tag][Ewido.TrackingCookie.Atdmt]
127.0.0.1  atlasdmt.com #[Panda.Spyware:Cookie/Atlas DMT]
127.0.0.1  www.atlasdmt.com
127.0.0.1  www.avenueainc.com
127.0.0.1  ads.adagent.chacha.com
127.0.0.1  ads.bidclix.com #[eTrust.BidClix]
127.0.0.1  www.bidclix.com
127.0.0.1  bidclix.net
127.0.0.1  www.bidclix.net
127.0.0.1  main.click-url.com #[SiteAdvisor.zango.com]
127.0.0.1  spd.netconversions.com
127.0.0.1  track.roiservice.com #[McAfee.Cookie-Roiservice]
# [Arundel Group][Harris Digital Publishing]
127.0.0.1  www.affiliatesuccess.net #[System Detective]
127.0.0.1  www.systemdetective.com #[Rogue/Suspect]
127.0.0.1  ztrack.net
# [Aster Edward Umali][Azter Inc]
127.0.0.1  www.azter.com #[SiteAdvisor.azter.com]
127.0.0.1  www.bestsexycelebs.com
127.0.0.1  www.hunkymalecelebs.com
127.0.0.1  missdanicapatrick.com
127.0.0.1  www.missdanicapatrick.com #[Win32/TrojanDownloader.Adload.NAY]
127.0.0.1  missjessicasimpson.com
127.0.0.1  www.missjessicasimpson.com #[W32/WinAd.GQ]
127.0.0.1  sexybabesx.com #[Win32/TrojanDownloader.Adload.NBH]
127.0.0.1  adrianalima.sexybabesx.com
127.0.0.1  aliciakeys.sexybabesx.com #[AdWare.Win32.WinAD.bv]
127.0.0.1  amandabynes.sexybabesx.com
127.0.0.1  angelina.sexybabesx.com
127.0.0.1  annakournikova.sexybabesx.com
127.0.0.1  annapaquin.sexybabesx.com
127.0.0.1  annehathaway.sexybabesx.com
127.0.0.1  ashanti.sexybabesx.com
127.0.0.1  ashleesimpson.sexybabesx.com
127.0.0.1  ashleyolsen.sexybabesx.com
127.0.0.1  audreytautou.sexybabesx.com
127.0.0.1  avrillavigne.sexybabesx.com
127.0.0.1  beyonce.sexybabesx.com
127.0.0.1  brianabanks.sexybabesx.com
127.0.0.1  britney.sexybabesx.com
127.0.0.1  brooke.sexybabesx.com
127.0.0.1  brookeburns.sexybabesx.com
127.0.0.1  cameron.sexybabesx.com
127.0.0.1  carmen.sexybabesx.com
127.0.0.1  charlizetheron.sexybabesx.com
127.0.0.1  christina.sexybabesx.com
127.0.0.1  christinaricci.sexybabesx.com
127.0.0.1  ciara.sexybabesx.com
127.0.0.1  danicapatrick.sexybabesx.com
127.0.0.1  danielahantuchova.sexybabesx.com
127.0.0.1  demimoore.sexybabesx.com
127.0.0.1  denise.sexybabesx.com
127.0.0.1  elishacuthbert.sexybabesx.com
127.0.0.1  emmawatson.sexybabesx.com
127.0.0.1  ericablasberg.sexybabesx.com
127.0.0.1  evagreen.sexybabesx.com
127.0.0.1  evalongoria.sexybabesx.com
127.0.0.1  gellar.sexybabesx.com
127.0.0.1  giselebundchen.sexybabesx.com
127.0.0.1  gwenstefani.sexybabesx.com
127.0.0.1  gwynethpaltrow.sexybabesx.com
127.0.0.1  halleberry.sexybabesx.com
127.0.0.1  heathergraham.sexybabesx.com
127.0.0.1  heatherlocklear.sexybabesx.com
127.0.0.1  heidiklum.sexybabesx.com
127.0.0.1  hilaryduff.sexybabesx.com
127.0.0.1  hilaryswank.sexybabesx.com
127.0.0.1  janetjackson.sexybabesx.com
127.0.0.1  jennajameson.sexybabesx.com
127.0.0.1  jenniferaniston.sexybabesx.com
127.0.0.1  jenniferellison.sexybabesx.com
127.0.0.1  jennifergarner.sexybabesx.com
127.0.0.1  jenniferlopez.sexybabesx.com
127.0.0.1  hewitt.sexybabesx.com
127.0.0.1  jessicaalba.sexybabesx.com
127.0.0.1  jessicabiel.sexybabesx.com
127.0.0.1  jessicasimpson.sexybabesx.com
127.0.0.1  jojo.sexybabesx.com
127.0.0.1  josiemaran.sexybabesx.com
127.0.0.1  jossstone.sexybabesx.com
127.0.0.1  juliaroberts.sexybabesx.com
127.0.0.1  juliastiles.sexybabesx.com
127.0.0.1  katebeckinsale.sexybabesx.com
127.0.0.1  katehudson.sexybabesx.com
127.0.0.1  katemoss.sexybabesx.com
127.0.0.1  katewinslet.sexybabesx.com
127.0.0.1  katieholmes.sexybabesx.com
127.0.0.1  keiraknightley.sexybabesx.com
127.0.0.1  kellyclarkson.sexybabesx.com
127.0.0.1  kristinkreuk.sexybabesx.com
127.0.0.1  leeleesobieski.sexybabesx.com
127.0.0.1  lindsay.sexybabesx.com #[Win32/Adware.WinAd]
127.0.0.1  livtyler.sexybabesx.com
127.0.0.1  lucyliu.sexybabesx.com
127.0.0.1  lucypinder.sexybabesx.com
127.0.0.1  madonna.sexybabesx.com
127.0.0.1  mandy.sexybabesx.com
127.0.0.1  sharapova.sexybabesx.com
127.0.0.1  mariahcarey.sexybabesx.com
127.0.0.1  marisamiller.sexybabesx.com
127.0.0.1  menasuvari.sexybabesx.com
127.0.0.1  michellerodriguez.sexybabesx.com
127.0.0.1  michellewie.sexybabesx.com #[Win32/TrojanDownloader.Adload.NAY]
127.0.0.1  milakunis.sexybabesx.com
127.0.0.1  millajovovich.sexybabesx.com
127.0.0.1  mischabarton.sexybabesx.com
127.0.0.1  monicabellucci.sexybabesx.com
127.0.0.1  naomicampbell.sexybabesx.com
127.0.0.1  naomiwatts.sexybabesx.com
127.0.0.1  nataliegulbis.sexybabesx.com
127.0.0.1  natalieportman.sexybabesx.com
127.0.0.1  nevecampbell.sexybabesx.com
127.0.0.1  nickyhilton.sexybabesx.com
127.0.0.1  nicolekidman.sexybabesx.com
127.0.0.1  nicolerichie.sexybabesx.com
127.0.0.1  nicolevaidisova.sexybabesx.com
127.0.0.1  pamela.sexybabesx.com
127.0.0.1  parishilton.sexybabesx.com
127.0.0.1  penelope.sexybabesx.com
127.0.0.1  rachelbilson.sexybabesx.com
127.0.0.1  rachelmcadams.sexybabesx.com
127.0.0.1  rachelstevens.sexybabesx.com
127.0.0.1  rachelweisz.sexybabesx.com
127.0.0.1  reese.sexybabesx.com
127.0.0.1  renee.sexybabesx.com
127.0.0.1  roselynsanchez.sexybabesx.com
127.0.0.1  salma.sexybabesx.com
127.0.0.1  samairearmstrong.sexybabesx.com
127.0.0.1  sandra.sexybabesx.com
127.0.0.1  saniamirza.sexybabesx.com
127.0.0.1  sashacohen.sexybabesx.com
127.0.0.1  scarlett.sexybabesx.com
127.0.0.1  selitaebanks.sexybabesx.com
127.0.0.1  serenawilliams.sexybabesx.com
127.0.0.1  shakira.sexybabesx.com
127.0.0.1  shannendoherty.sexybabesx.com
127.0.0.1  sharonstone.sexybabesx.com
127.0.0.1  sherylcrow.sexybabesx.com
127.0.0.1  siennamiller.sexybabesx.com
127.0.0.1  sophiabush.sexybabesx.com
127.0.0.1  stacykeibler.sexybabesx.com
127.0.0.1  terapatrick.sexybabesx.com
127.0.0.1  terihatcher.sexybabesx.com
127.0.0.1  thorabirch.sexybabesx.com
127.0.0.1  tyrabanks.sexybabesx.com
127.0.0.1  umathurman.sexybabesx.com
127.0.0.1  venuswilliams.sexybabesx.com
127.0.0.1  www.sexybabesx.com #[AVG.Generic.MUM]
# [Azoogle.com INC][Impulse Leads]
127.0.0.1  i.1100i.com
127.0.0.1  images.1100i.com
127.0.0.1  www.adroz.com #[affiliate][AIM Smileys]
127.0.0.1  c.azjmp.com #[SpySweeper.Spy.Cookie][Adware-Fizzle]
127.0.0.1  i.azjmp.com
127.0.0.1  x.azjmp.com
127.0.0.1  www.azjmp.com
127.0.0.1  images.azoogleads.com
127.0.0.1  images.azooimages.com
127.0.0.1  www.azoogleads.com
127.0.0.1  b1.bluetime.com
127.0.0.1  www.bluetime.com
127.0.0.1  www.giftfox.com
127.0.0.1  images.hostimages.net
127.0.0.1  images.imagesbyaz.com
127.0.0.1  images.imgehost.com
127.0.0.1  impulseleads.com
127.0.0.1  www.impulseleads.com
127.0.0.1  images.imgserver.net
127.0.0.1  www.merchantportal.com
127.0.0.1  www.mport.com
127.0.0.1  www.mptrack.com #[Whois.Blacklisted][server down?]
127.0.0.1  www.mydishprovider.com
127.0.0.1  noadware.biz
127.0.0.1  www.noadware.biz #[hop.clickbank.net]
127.0.0.1  c.qckjmp.com
127.0.0.1  visit-link.com
# [Aztec Marketing][West Frontier Holdings][Offshorefleet Holdings S.A]
127.0.0.1  artella.biz #[AdWare.Win32.BHO.bh]
127.0.0.1  home.artella.biz
127.0.0.1  www.artella.biz
127.0.0.1  www2.click2begin.com
127.0.0.1  www3.click2begin.com
127.0.0.1  clickfast.biz #[SunBelt.Ezula.ClickFast]
127.0.0.1  www.clickfast.biz
127.0.0.1  www2.hooowah.com
127.0.0.1  www3.hooowah.com
127.0.0.1  www4.hooowah.com
127.0.0.1  www5.hooowah.com
127.0.0.1  www6.hooowah.com
127.0.0.1  www7.hooowah.com
127.0.0.1  www8.hooowah.com
127.0.0.1  www9.hooowah.com
127.0.0.1  www10.hooowah.com
127.0.0.1  www.hooowah.com
127.0.0.1  iconads.biz
127.0.0.1  www.iconads.biz #[SunBelt.AdRotator/IconAds][trafficsector.com]
127.0.0.1  www.pops-stop.com #[Spyware.SafeSurfing][trafficsector.com]
127.0.0.1  www1.pops-stop.com
127.0.0.1  popupsearches.com
127.0.0.1  www2.popupsearches.com
127.0.0.1  www.popupsearches.com #[SunBelt.PopUpSearches.com]
127.0.0.1  trafficsector.com #[Adware.Webext][SunBelt.SafeSurfing.RsyncMon]
127.0.0.1  new.trafficsector.com #[McAfee.Adware-Iconads]
127.0.0.1  www.trafficsector.com #[McAfee.Adware-BitLocker]
# [Actif Oiseau Alerte S.A.][Janerus, Inc][Mnetpower LTD]
127.0.0.1  www.adultmegaporn.com
127.0.0.1  www.eaffiliateinc.com
127.0.0.1  www.ewebadserver.com #[Begin2Search]
127.0.0.1  gpstool.globaladserver.com #[Win32/Adware.Beginto]
127.0.0.1  www.globaladserver.com
127.0.0.1  globalwebsearch.com #[Parasite.ILookup]
127.0.0.1  www.globalwebsearch.com #[Adware.ILookup]
127.0.0.1  goldmembersarea.com
127.0.0.1  www.goldmembersarea.com
127.0.0.1  gophersearch.com #[McAfee.Adware-WorldAnywhere]
127.0.0.1  www.gophersearch.com
127.0.0.1  secure.ivirtualcard.com
127.0.0.1  secure.memberareaplus.com
127.0.0.1  www.mnetpower.com
127.0.0.1  secure.pinkpays.com
127.0.0.1  www.pinkpays.com
127.0.0.1  vroomsearch.com
127.0.0.1  www.vroomsearch.com
# [BannerCPM]
127.0.0.1  bannercpm.com
127.0.0.1  www.bannercpm.com
127.0.0.1  cpmadz.com
127.0.0.1  www.cpmadz.com #[AdWare.Win32.TrafficSol.e]
127.0.0.1  mycpmads.com #[SunBelt.MyCPMAds Browser Optimizer]
127.0.0.1  www.mycpmads.com
# [Bariscloth INC][Daniel Wesley]
127.0.0.1  www.aimface.com
127.0.0.1  www.buddy-icons.us #[Kephyr.PUP]
127.0.0.1  www.funnyjoke.net
127.0.0.1  www.imbuddy.net #[Trojan-Dropper.Win32.ExeBundle.286]
127.0.0.1  www.ratepic.com
# [Belcaro Group][eTrust.Spyware.Belcaro GoldenRetriever]
127.0.0.1  1cat.com
127.0.0.1  i.1cat.com
127.0.0.1  www.1cat.com
127.0.0.1  gr1.cc
127.0.0.1  gr2.cc
127.0.0.1  gr3.cc
127.0.0.1  gr4.cc
127.0.0.1  selectbonus.com
127.0.0.1  www.selectbonus.com
127.0.0.1  www.shopathome.com
127.0.0.1  shopathomeselect.com #[AdWare.Win32.Sahat.ad]
127.0.0.1  downloads.shopathomeselect.com #[Win32/Adware.SAHAgent]
127.0.0.1  www.shopathomeselect.com #[Adware.SAHAgent]
# [Bell Globemedia Interactive Inc]
127.0.0.1  adcounter.theglobeandmail.com
127.0.0.1  adrates.theglobeandmail.com
127.0.0.1  ads.globeandmail.com
127.0.0.1  ads1.theglobeandmail.com
127.0.0.1  visit.theglobeandmail.com
127.0.0.1  www1.theglobeandmail.com
# [Ben Vanderbildt]
127.0.0.1  www.albumgalaxy.com #[AdWare.Win32.Relevant.a]
127.0.0.1  www.kiwialpha.com #[SiteAdvisor.kiwialpha.com]
127.0.0.1  www.twistermp3.com #[AdWare.Win32.Relevant.a]
# [Bit Wise Publishing, LLC]
127.0.0.1  www.bitwisepublishing.com #[myglobalsearch.com]
127.0.0.1  www.free-patriotic-screensavers.com #[tafmaster.com]
127.0.0.1  www.my247eshop.com #[eShopper Search Bar]
127.0.0.1  www.scenicreflections.com #[SiteAdvisor.scenicreflections.com]
# [Bluestreak][Tracking Service]
127.0.0.1  bluestreak.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ak.bluestreak.com
127.0.0.1  ca1.bluestreak.com #[SunBelt.Bluestreak.com][a2.x.akamai.net]
127.0.0.1  fr.bluestreak.com
127.0.0.1  ion.bluestreak.com
127.0.0.1  s0.bluestreak.com #[Ewido.TrackingCookie.Bluestreak]
127.0.0.1  s0b.bluestreak.com #[SiteAdvisor.aim.com]
127.0.0.1  s2.bluestreak.com #[McAfee.Cookie-Bluestreak]
127.0.0.1  s3.bluestreak.com
127.0.0.1  s4.bluestreak.com
127.0.0.1  s5.bluestreak.com #[Panda.Spyware:Cookie/Bluestreak]
127.0.0.1  s6.bluestreak.com
127.0.0.1  s7.bluestreak.com #[Tenebril.Tracking.Cookie]
127.0.0.1  s8.bluestreak.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.bluestreak.com
# [Bluetide Software][DeluxeCommunications]
127.0.0.1  www.bluetidesoftware.com #[SiteAdvisor.bluetidesoftware.com]
127.0.0.1  dxcdirect.com
127.0.0.1  dl.dxcdirect.com
127.0.0.1  media.dxcdirect.com
127.0.0.1  search.dxcdirect.com
127.0.0.1  www.dxcdirect.com
127.0.0.1  www.mycustomersdirect.com
127.0.0.1  surfsidekick.com #[ADW_SURFKICK.B]
127.0.0.1  ads.surfsidekick.com #[McAfee.Adware-SurfSideKick.dr]
127.0.0.1  dl.surfsidekick.com #[Parasite.TVMedia.SSK][TROJ_SMALL.AQC]
127.0.0.1  search.surfsidekick.com #[Panda.Spyware/SurfSideKick]
127.0.0.1  www.surfsidekick.com #[Adware.SurfSideKick]
# [Bob Jones][Tommy Davis][Adware.BlockChecker]
127.0.0.1  www.block-checker.com #[McAfee.Adclicker-DF]
127.0.0.1  www.system-processes.com #[Adware.SystemProcess]
# [Bobi Net]
127.0.0.1  secure.certone.com #[Adware.WebDir][SunBelt.WebDir]
127.0.0.1  www.filefront.net
127.0.0.1  www.gizmoyo.com
127.0.0.1  www.torrentsearcher.net
127.0.0.1  www.xcode.info
127.0.0.1  files.xeol.net #[SiteAdvisor.xeol.net]
127.0.0.1  pr.xeol.net
# [Bonzi Software][Adware.Bonzi]
127.0.0.1  download.bonzi.com
127.0.0.1  images.bonzi.com
127.0.0.1  www.bonzi.com #[ADW_BONJING.A]
127.0.0.1  www.bonzibuddy.com
# [Boua Pcl][Sen Boua]
127.0.0.1  musah.info #[Trojan-Downloader.Win32.Delf.h][TROJ_DLOADER.AFB]
127.0.0.1  ownusa.info #[Trojan-Clicker.Agent.8]
# [BraveNet][Tracking Service]
127.0.0.1  bravenet.com #[Tenebril.Tracking.Cookie]
127.0.0.1  adserv.bravenet.com #[McAfee.Cookie-Bravenet]
127.0.0.1  counter1.bravenet.com
127.0.0.1  counter2.bravenet.com
127.0.0.1  counter3.bravenet.com
127.0.0.1  counter4.bravenet.com
127.0.0.1  counter5.bravenet.com
127.0.0.1  counter6.bravenet.com
127.0.0.1  counter7.bravenet.com
127.0.0.1  counter8.bravenet.com
127.0.0.1  counter9.bravenet.com
127.0.0.1  counter10.bravenet.com
127.0.0.1  counter11.bravenet.com
127.0.0.1  counter12.bravenet.com
127.0.0.1  counter13.bravenet.com
127.0.0.1  counter14.bravenet.com
127.0.0.1  counter15.bravenet.com
127.0.0.1  counter16.bravenet.com
127.0.0.1  counter17.bravenet.com
127.0.0.1  counter18.bravenet.com #[Panda.Spyware:Cookie/bravenetA]
127.0.0.1  counter19.bravenet.com
127.0.0.1  counter20.bravenet.com
127.0.0.1  counter21.bravenet.com
127.0.0.1  counter22.bravenet.com
127.0.0.1  counter23.bravenet.com
127.0.0.1  counter24.bravenet.com
127.0.0.1  counter25.bravenet.com
127.0.0.1  counter26.bravenet.com
127.0.0.1  counter27.bravenet.com
127.0.0.1  counter28.bravenet.com
127.0.0.1  counter29.bravenet.com
127.0.0.1  counter30.bravenet.com
127.0.0.1  counter31.bravenet.com
127.0.0.1  counter32.bravenet.com
127.0.0.1  counter33.bravenet.com
127.0.0.1  counter34.bravenet.com
127.0.0.1  counter35.bravenet.com
127.0.0.1  counter36.bravenet.com
127.0.0.1  counter37.bravenet.com
127.0.0.1  counter38.bravenet.com
127.0.0.1  counter39.bravenet.com
127.0.0.1  counter40.bravenet.com
127.0.0.1  counter41.bravenet.com
127.0.0.1  counter42.bravenet.com
127.0.0.1  counter43.bravenet.com
127.0.0.1  counter44.bravenet.com
127.0.0.1  counter45.bravenet.com
127.0.0.1  counter46.bravenet.com
127.0.0.1  counter47.bravenet.com
127.0.0.1  counter48.bravenet.com
127.0.0.1  counter49.bravenet.com
127.0.0.1  counter50.bravenet.com
127.0.0.1  images.bravenet.com #[SecuritySpace.WebBug]
127.0.0.1  linktrack.bravenet.com #[SunBelt.Bravenet.com]
127.0.0.1  pub2.bravenet.com #[Bravenet.com Service Code]
127.0.0.1  pub12.bravenet.com
127.0.0.1  pub16.bravenet.com
127.0.0.1  pub23.bravenet.com
127.0.0.1  pub27.bravenet.com
127.0.0.1  pub28.bravenet.com
127.0.0.1  pub30.bravenet.com
127.0.0.1  pub31.bravenet.com
127.0.0.1  pub39.bravenet.com
127.0.0.1  pub40.bravenet.com
127.0.0.1  pub42.bravenet.com
127.0.0.1  pub45.bravenet.com
127.0.0.1  pub49.bravenet.com
127.0.0.1  xml.bravenet.com #[Ad-Aware.Tracking.Cookie]
# [BrowserMedia / BuyDomains.com]
127.0.0.1  bannerx.seeq.com
127.0.0.1  smds.seeq.com
# [BUDS Inc. Ad Network][SPYW_SOFTOMATE.A]
127.0.0.1  www.addfreegames.com
127.0.0.1  affiliate.budsinc.com #[directtrack.com]
127.0.0.1  content.budsinc.com
127.0.0.1  show.budsinc.com
127.0.0.1  www.budsinc.com
127.0.0.1  www.musicfeet.com
127.0.0.1  www.noadnetwork.com
# [BurstMedia][Tracking Service]
127.0.0.1  ads.addesktop.com #[McAfee.Cookie-Addesktop]
127.0.0.1  www.burstbeacon.com #[Panda.Spyware:Cookie/BurstBeacon]
127.0.0.1  burstmedia.com
127.0.0.1  roscoe.burstmedia.com #[SunBelt.BurstMedia]
127.0.0.1  survey.burstmedia.com
127.0.0.1  web.burstmedia.com
127.0.0.1  websurvey.burstmedia.com
127.0.0.1  ads.burstnet.com #[SpySweeper.Spy.Cookie]
127.0.0.1  gifs.burstnet.com
127.0.0.1  sj.burstnet.com #[SunBelt.BurstNet]
127.0.0.1  te.burstnet.com
127.0.0.1  text.burstnet.com
127.0.0.1  www.burstnet.com #[eTrust.Tracking.Cookie]
127.0.0.1  www2.burstnet.com
127.0.0.1  www3.burstnet.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www4.burstnet.com
127.0.0.1  www5.burstnet.com
127.0.0.1  www6.burstnet.com
127.0.0.1  www.burstnet.akadns.net
# [Casale Media][Comspec Communications]
127.0.0.1  casalemedia.com #[McAfee.Cookie-Casalemedia]
127.0.0.1  as.casalemedia.com #[Ewido.TrackingCookie.Casalemedia]
127.0.0.1  b.casalemedia.com #[a1083.g.akamai.net][McAfee.Adware-SrchExplorer]
127.0.0.1  c.casalemedia.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  i.casalemedia.com #[Tenebril.Tracking.Cookie]
127.0.0.1  img.casalemedia.com #[SunBelt.casalemedia.com]
127.0.0.1  js.casalemedia.com #[a883.g.akamai.net]
127.0.0.1  lb01.casalemedia.com #[SpySweeper.Spy.Cookie]
127.0.0.1  r.casalemedia.com #[Symantec.SpywareStormer]
127.0.0.1  www.casalemedia.com
127.0.0.1  www.oofun.com
127.0.0.1  00fun.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.00fun.com
# [Cassava Enterprises]
127.0.0.1  chat.888.com #[SiteAdvisor.888.com]
127.0.0.1  free.888.com #[Panda.Spyware:Cookie/888]
127.0.0.1  images.888.com
127.0.0.1  setupspcp1.888.com
127.0.0.1  www.888.com #[McAfee.Adware-CasOnline]
127.0.0.1  casino-on-net.com
127.0.0.1  demogwa.casino-on-net.com
127.0.0.1  images.casino-on-net.com
127.0.0.1  java2.casino-on-net.com
127.0.0.1  www.casino-on-net.com #[SunBelt.CasinoOnNet]
127.0.0.1  www.casinoonnet.com #[eTrust.CasinoOnNet]
127.0.0.1  download1.pacificpoker.com
127.0.0.1  free.pacificpoker.com
127.0.0.1  images.pacificpoker.com #[SunBelt.PacificPoker]
127.0.0.1  playersclub.reefclubcasino.com
127.0.0.1  www.pacificpoker.com #[AdWare.Win32.Casino.m]
127.0.0.1  www.reefclubcasino.com
# [c2 Media Ltd Group][Circle Developement Ltd]
127.0.0.1  aavc.com
127.0.0.1  www.adserver5.com
127.0.0.1  active-max.com
127.0.0.1  search.active-max.com
127.0.0.1  www.active-max.com
127.0.0.1  allaboutsearching.com
127.0.0.1  www.allaboutsearching.com
127.0.0.1  amazingautossearch.com
127.0.0.1  www.amazingautossearch.com
127.0.0.1  cidhelp.com
127.0.0.1  contexualsearch.com
127.0.0.1  www.contexualsearch.com
127.0.0.1  www.dialup2.com
127.0.0.1  dns-look-up.com
127.0.0.1  ads.dns-look-up.com #[Win32/TrojanDownloader.Swizzor]
127.0.0.1  ayb.dns-look-up.com #[TR/Swizzor.A][AdWare.Win32.Lop.ag]
127.0.0.1  nb.dns-look-up.com
127.0.0.1  upd.dns-look-up.com
127.0.0.1  ecpm.com #[ADW_BADBITOR.A]
127.0.0.1  www.ecpm.com
127.0.0.1  look-today.com
127.0.0.1  www.look-today.com
127.0.0.1  lop.com #[Wildcard DNS]
127.0.0.1  ao.lop.com
127.0.0.1  ayb.lop.com #[McAfee.Swizzor]
127.0.0.1  bins.lop.com
127.0.0.1  k17177.bins.lop.com
127.0.0.1  img.lop.com
127.0.0.1  sue.lop.com
127.0.0.1  srch.lop.com
127.0.0.1  d4308.upd.lop.com #[McAfee.Swizzor]
127.0.0.1  r25407.upd.lop.com
127.0.0.1  upd.lop.com
127.0.0.1  www1.lop.com
127.0.0.1  www.lop.com
127.0.0.1  maxexp.com
127.0.0.1  ayb.maximumexperience.com #[McAfee.Swizzor]
127.0.0.1  www.mp3search.com #[Panda.Spyware:Cookie/Mp3search]
127.0.0.1  mysearchnow.com
127.0.0.1  search200.com #[eTrust.Search200 Toolbar]
127.0.0.1  www.search200.com #[ADW_BADBITOR.A]
127.0.0.1  search.mysearchnow.com
127.0.0.1  www.mysearchnow.com
127.0.0.1  ads.netbios-wait.com
127.0.0.1  ayb.netbios-wait.com
127.0.0.1  www.netbios-wait.com #[Adware.Memini]
127.0.0.1  netsearchsoft.com #[Adware.Memini]
127.0.0.1  www.netsearchsoft.com
127.0.0.1  omegasearch.com
127.0.0.1  www.omegasearch.com
127.0.0.1  prosearching.com #[McAfee.Adware-WinActive]
127.0.0.1  www.prosearching.com
127.0.0.1  search.rub.to #[Adware.Trinity]
127.0.0.1  www.rub.to
127.0.0.1  sbvr.com
127.0.0.1  www.sbvr.com
127.0.0.1  searchexe.com
127.0.0.1  www.searchexe.com
127.0.0.1  searchweb2.com
127.0.0.1  www.searchweb2.com
127.0.0.1  spawnet.com
127.0.0.1  www.spawnet.com
127.0.0.1  tdmy.com #[TrojanDownloader.Win32.Swizzor.h]
127.0.0.1  tefs.com
127.0.0.1  tfil.com
127.0.0.1  www.tfil.com
127.0.0.1  tdko.com
127.0.0.1  www.tdko.com
127.0.0.1  ayb.trinityacquisitions.com #[McAfee.Swizzor][Wildcard DNS]
127.0.0.1  www.wabu.com
127.0.0.1  wfix.com #[SunBelt.WFix.com]
127.0.0.1  ads.zone-media.com #[Troj/Swizzor-CN][TROJ_SWIZZOR.EJ]
127.0.0.1  ayb.zone-media.com
127.0.0.1  www.zone-media.com
# [Cash4Downloads][CidHelp Group]
127.0.0.1  www.3wplayer.com #[Symantec.3wPlayer]
127.0.0.1  bitdownload.org
127.0.0.1  www.bitdownload.org
127.0.0.1  www.bitgrabber.com
127.0.0.1  www.bitroll.com #[AdWare.Win32.Lop.bo]
127.0.0.1  bitsofporn.com
127.0.0.1  www.bitsofporn.com
127.0.0.1  c4dl.com
127.0.0.1  www.c4dl.com
127.0.0.1  www.cash4downloads.com
127.0.0.1  www.get-torrent.com #[AdWare.Win32.Lop.bo]
127.0.0.1  addisen.imageswap.com
127.0.0.1  download.netpumper.com
127.0.0.1  www.netpumper.com #[Symantec.NetPumper][SiteAdvisor.NetPumper]
127.0.0.1  download.play3w.com
127.0.0.1  go.play3w.com
127.0.0.1  playon.play3w.com #[Trojan.Dldr.Swizzor.C]
127.0.0.1  plugindl.com
127.0.0.1  www.plugindl.com
127.0.0.1  www.torrent101.com #[Trojan.Win32.Obfuscated.en]
127.0.0.1  www.torrentq.com
127.0.0.1  www.winzix.com #[Symantec.WinZix][FraudTool.Win32.WinZix.a]
# [CA Web Designs][Tracking Service]
127.0.0.1  clickxchange.com #[SunBelt.Clickxchange.com]
127.0.0.1  caweb1.clickxchange.com
127.0.0.1  caweb2.clickxchange.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.clickxchange.com
# [Chunkybreakfast][Robert Davidson]
127.0.0.1  elitemediagroup.net #[Trojan.TrustedZone]
127.0.0.1  affiliates.elitemediagroup.net
127.0.0.1  bins.elitemediagroup.net
127.0.0.1  cabs.elitemediagroup.net #[Win32/Adware.MediaMotor]
127.0.0.1  logs.elitemediagroup.net
127.0.0.1  mmm.elitemediagroup.net
127.0.0.1  www.elitemediagroup.net #[SpySweeper.elitemediagroup-mediamotor]
127.0.0.1  pokahaus.com
# [Chitika]
127.0.0.1  ads.chitika.net
127.0.0.1  ads1.chitika.net
127.0.0.1  blogads.chitika.net
127.0.0.1  ca.chitika.net
127.0.0.1  mm.chitika.net
127.0.0.1  scripts.chitika.net
# [CJB Management][Backdoor.Ptsnoop]
127.0.0.1  bannerexchange.cjb.net
127.0.0.1  coder3862004.cjb.net #[Trojan.Bansap]
127.0.0.1  dialer.cjb.net #[HJTH.DirectPlugin Dialer]
127.0.0.1  crashtest.cjb.net
# [Claria Corporation][GAIN Publishing]
127.0.0.1  www.behaviorlink.com
127.0.0.1  ath.belnk.com #[Panda.Spyware:Cookie/Belnk]
127.0.0.1  art.ath.belnk.com #[McAfee.Cookie-Belnk]
127.0.0.1  dist.belnk.com #[Adware-Adlogix]
127.0.0.1  sio.belnk.com
127.0.0.1  sio.balance.belnk.com
127.0.0.1  content.dashbar.com
127.0.0.1  results.dashbar.com #[Adware.DashBar][SPYW_DASHBAR.300]
127.0.0.1  www.dashbar.com #[eTrust.Spyware.Claria.Dashbar]
127.0.0.1  www.date-manager.com #[SunBelt.Claria.DateManager][Adware.DateManager]
127.0.0.1  www.entrypass.com
127.0.0.1  download.gainpublishing.com #[SiteAdvisor.precision-time.com]
127.0.0.1  www.gainpublishing.com
127.0.0.1  www.gatorcorporation.com
127.0.0.1  www.gatoradvertisinginformationnetwork.com
127.0.0.1  gator.com #[SPYW_GATOR.F]
127.0.0.1  bc2.gator.com #[SPYW_GATOR.B]
127.0.0.1  bg.gator.com
127.0.0.1  bg2.gator.com
127.0.0.1  bi.gator.com
127.0.0.1  coupons.gator.com
127.0.0.1  creative.gator.com #[webstage-1.gator.com]
127.0.0.1  dmz-gi01.gator.com
127.0.0.1  gator29.gator.com
127.0.0.1  gatorcme.gator.com
127.0.0.1  gatortime.gator.com
127.0.0.1  gi.gator.com
127.0.0.1  content.balance.gator.com
127.0.0.1  gs.balance.gator.com
127.0.0.1  gt.balance.gator.com
127.0.0.1  search.balance.gator.com #[SiteAdvisor.fish-screensaver.com]
127.0.0.1  trickle.balance.gator.com
127.0.0.1  web.balance.gator.com
127.0.0.1  xmlsearch.balance.gator.com
127.0.0.1  gt.gator.com
127.0.0.1  images.gator.com
127.0.0.1  map.gator.com
127.0.0.1  papps.gator.com
127.0.0.1  search.gator.com
127.0.0.1  updateserver.gator.com
127.0.0.1  weather.gator.com
127.0.0.1  xmlsearch.gator.com
127.0.0.1  www.gator.com #[Adware.GatorEWallet][ADW_GAIN.A]
127.0.0.1  www.gotsmiley.com #[Adware.GotSmiley][PcTools.GotSmily]
127.0.0.1  www.offercompanion.com #[eTrust.Offer Companion]
127.0.0.1  www.precision-time.com #[Adware.PrecisionTime]
127.0.0.1  www.relevancyrank.com #[IE-SpyAd]
127.0.0.1  www.screenscenes.com #[Adware.ScreenScenes]
127.0.0.1  content.searchscout.com
127.0.0.1  www.searchscout.com #[Adware.SearchScout]
127.0.0.1  www.smartbar.com
127.0.0.1  www.tgcsearch.com
127.0.0.1  qazone5.thegatornetwork.com
127.0.0.1  www.weatherscope.com #[SunBelt.Claria.WeatherScope]
127.0.0.1  www.websecurealert.com #[Adware.WebSecureAlert][ADW_WSECALERT.A]
# [ClickSpring LLC][Daniel Houston][Downloader-EV]
127.0.0.1  www.clicklinks.net
127.0.0.1  clickspring.net #[Trojan.TrustedZones]
127.0.0.1  cu.clickspring.net #[server down?]
127.0.0.1  fp.clickspring.net #[Adware.PurityScan.C][server down?]
127.0.0.1  nf.clickspring.net #[eTrust.Win32.Clspring][server down?]
127.0.0.1  pisces.clickspring.net #[server down?]
127.0.0.1  www.clickspring.net #[TROJ_MENDWAR.A]
127.0.0.1  jimmysurf.com #[JimmySurf][SurfProtect]
127.0.0.1  www.jimmysurf.com
127.0.0.1  www2.jimmysurf.com
127.0.0.1  www.marketprecision.net
127.0.0.1  www.mediatickets.net #[Parasite.MediaTickets]
127.0.0.1  www.mediaprecision.net
127.0.0.1  www.oinadserve.com
127.0.0.1  outerinfo.com
127.0.0.1  campaigns.outerinfo.com #[ADW_PURITYSCAN.I]
127.0.0.1  campaigns2.outerinfo.com #[ADW_VALUEAD.M]
127.0.0.1  cu.outerinfo.com
127.0.0.1  nf.outerinfo.com
127.0.0.1  update.outerinfo.com
127.0.0.1  update2.outerinfo.com #[McAfee.Adware-ClickSpring]
127.0.0.1  www.outerinfo.com
127.0.0.1  www.pornstertv.com #[Win32/TrojanDownloader.PurityScan]
127.0.0.1  purityscan.com #[Adware.Purityscan]
127.0.0.1  www.purityscan.com #[TROJ_MENDWAR.A]
127.0.0.1  tizzletalk.com
127.0.0.1  www2.tizzletalk.com
127.0.0.1  www3.tizzletalk.com
127.0.0.1  www6.tizzletalk.com
127.0.0.1  www7.tizzletalk.com
127.0.0.1  www.tizzletalk.com
127.0.0.1  ucbill.com #[Adware.ClickDLoader]
127.0.0.1  www.ucbill.com
127.0.0.1  www.virtuescope.com #[SunBelt.Adw.Purityscan.Virtuescope]
127.0.0.1  windsorpearl.com #[Parasite.PurityScan]
127.0.0.1  www.windsorpearl.com
127.0.0.1  yazzle.net #[NOD32.Win32/Adware.MediaTickets]
127.0.0.1  ads.yazzle.net
127.0.0.1  partners.yazzle.net
127.0.0.1  yax-download.yazzle.net #[AdWare.Win32.MediaTickets.w]
127.0.0.1  www.yazzle.net #[SunBelt.Adw.Yazzle.Sudoku][Adware.Yazzle]
127.0.0.1  www.zolero.com
# [CNN/Time Warner/AOL]
127.0.0.1  ads.web.aol.com
127.0.0.1  affiliate.aol.com
127.0.0.1  dynamic.aol.com
127.0.0.1  free.aol.com
127.0.0.1  ar.atwola.com
127.0.0.1  ar1.atwola.com
127.0.0.1  ar7.atwola.com #[McAfee.Cookie-Atwola]
127.0.0.1  ar9.atwola.com
127.0.0.1  pr.atwola.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads.newline.aol.com
127.0.0.1  ads.cartoonnetwork.com
127.0.0.1  ads.cnn.com
127.0.0.1  ads.aol.co.uk
127.0.0.1  adremote.pathfinder.com
127.0.0.1  metrics.si.com #[aolturnersi.122.2o7.net]
127.0.0.1  adremote.timeinc.net
# [CNET Networks]
127.0.0.1  as.cmpnet.com #[DartRichMedia]
127.0.0.1  datapop.cmpnet.com
127.0.0.1  cookies.cmpnet.com
127.0.0.1  adimg.cnet.com
127.0.0.1  mads.cnet.com
127.0.0.1  remotead-internal.cnet.com
127.0.0.1  remotead.cnet.com
127.0.0.1  ads.com.com
127.0.0.1  adimg.com.com
127.0.0.1  adlog.com.com
127.0.0.1  mads.com.com
127.0.0.1  adinterax.cnet.com.edgesuite.net
127.0.0.1  adimg.download.com
127.0.0.1  mads.download.com
127.0.0.1  mads.gamefaqs.com
127.0.0.1  mads.gamespot.com
127.0.0.1  n.news.com #[news.com.112.2o7.net]
127.0.0.1  adimg.tv.com
127.0.0.1  mads.tv.com
127.0.0.1  ads.webshots.com
127.0.0.1  mads.webshots.com #[madison_ad]
127.0.0.1  ads.zdnet.com
127.0.0.1  adimg.zdnet.com
127.0.0.1  mads.zdnet.com
127.0.0.1  tracker.zdnet.com.au #[WebBug]
# [Cnzz]
127.0.0.1  js.cnzz.com
127.0.0.1  s1.cnzz.com
127.0.0.1  s3.cnzz.com
127.0.0.1  s4.cnzz.com
127.0.0.1  s11.cnzz.com
127.0.0.1  s12.cnzz.com
127.0.0.1  s18.cnzz.com
127.0.0.1  s19.cnzz.com
127.0.0.1  s26.cnzz.com
127.0.0.1  s28.cnzz.com
127.0.0.1  s29.cnzz.com
127.0.0.1  s34.cnzz.com
127.0.0.1  s37.cnzz.com
127.0.0.1  s48.cnzz.com
127.0.0.1  s50.cnzz.com
127.0.0.1  s51.cnzz.com
127.0.0.1  s54.cnzz.com
127.0.0.1  s55.cnzz.com
127.0.0.1  s62.cnzz.com
127.0.0.1  s63.cnzz.com
127.0.0.1  s66.cnzz.com
127.0.0.1  s80.cnzz.com
127.0.0.1  s83.cnzz.com
127.0.0.1  s94.cnzz.com
127.0.0.1  s99.cnzz.com
127.0.0.1  s101.cnzz.com
127.0.0.1  s102.cnzz.com
127.0.0.1  s103.cnzz.com
127.0.0.1  s105.cnzz.com
127.0.0.1  s106.cnzz.com
127.0.0.1  s108.cnzz.com
127.0.0.1  s109.cnzz.com
127.0.0.1  s110.cnzz.com
127.0.0.1  s111.cnzz.com
127.0.0.1  s112.cnzz.com
127.0.0.1  s113.cnzz.com
127.0.0.1  s115.cnzz.com
127.0.0.1  s116.cnzz.com
127.0.0.1  s118.cnzz.com
127.0.0.1  s120.cnzz.com
127.0.0.1  v1.cnzz.com
127.0.0.1  v4.cnzz.com
127.0.0.1  v5.cnzz.com
127.0.0.1  v9.cnzz.com
# [College Publisher][Viacom International]
127.0.0.1  stats.broadbandpublisher.com
127.0.0.1  admanager2.broadbandpublisher.com
127.0.0.1  admanager3.collegepublisher.com
127.0.0.1  localads.collegepublisher.com
# [CommonName Limited][Adware.CommonName][Parasite.CommonName]
127.0.0.1  commonname.com
127.0.0.1  www.commonname.com #[AdWare.CommonName.l]
127.0.0.1  commonnames.com
127.0.0.1  www.commonnames.com
127.0.0.1  www.kpsn.com
127.0.0.1  trafficexplorer.com
127.0.0.1  www.trafficexplorer.com #[AdWare.CommonName.g]
127.0.0.1  xpsn.com #[McAfee.Adware-CommonName.dll]
127.0.0.1  search.xpsn.com
127.0.0.1  www.xpsn.com
# [Conducive]
127.0.0.1  bridge.admarketplace.net
127.0.0.1  www.admarketplace.net
127.0.0.1  ads.cc214142.com #[adbureau.net][McAfee.Adware-CasClient]
127.0.0.1  ad.cs102175.com #[ads.admarketplace.net]
# [Contextu Ads]
127.0.0.1  bigapple.contextuads.com
127.0.0.1  cowboy.contextuads.com
127.0.0.1  tag.contextweb.com
127.0.0.1  www2.contextweb.com
127.0.0.1  www3.contextweb.com
127.0.0.1  www5.contextweb.com
127.0.0.1  www7.contextweb.com
127.0.0.1  www.contextuads.com #[F-Secure.ContextuAd]
127.0.0.1  www.nicheseek.com
127.0.0.1  www2.nicheseek.com
# [CWS related and Major Affiliates]
127.0.0.1  a7search.com
127.0.0.1  www.a7search.com
127.0.0.1  acc.count-all.com #[CWS.Tapicfg][rl.webtracer.cc]
127.0.0.1  www.coolfreehost.com
127.0.0.1  prx.freecj.com #[MHTMLRedir.Exploit]
127.0.0.1  www.findin.org
127.0.0.1  firstbookmark.com #[Parasite.ClientMan]
127.0.0.1  www.firstbookmark.com
127.0.0.1  freepage.ws
127.0.0.1  globe-finder.net #[clearsearch.net]
127.0.0.1  www.globe-finder.net
127.0.0.1  global-finder.com #[CWS.Msinfo][server down?]
127.0.0.1  www.global-finder.com
127.0.0.1  itseasy.us #[McAfee.Startpage-YBM]
127.0.0.1  lustler.com
127.0.0.1  www.lustler.com
127.0.0.1  makechoice.com #[McAfee.QlowZones-25]
127.0.0.1  www.makechoice.com #[MHTMLRedir.Exploit]
127.0.0.1  www.mywebsearch.net
127.0.0.1  ne-ebu.com
127.0.0.1  ntsearch.com #[MHTMLRedir.Exploit][mwsfeed.php]
127.0.0.1  www.ntsearch.com #[Trojan.Win32.Spooner.d][Adware-NSearch]
127.0.0.1  rdposters.com #[Trojan.Win32.Adex.a]
127.0.0.1  security-updater.com #[Win32.Wintrim.AG]
127.0.0.1  www.security-updater.com #[Trojan.Skintrim]
127.0.0.1  shop.sexplorer.it
127.0.0.1  www.sexplorer.it
127.0.0.1  t.rack.cc #[TROJ_SEEKER.B]
127.0.0.1  roquvp.t.rack.cc
127.0.0.1  tjdjuz.t.rack.cc
127.0.0.1  uhrnyk.t.rack.cc
127.0.0.1  teen-biz.com #[Trojan.Win32.StartPage.bh][IFrame.Exploit]
127.0.0.1  temasearch.com #[topsearch10.com]
127.0.0.1  www.temasearch.com
127.0.0.1  the-exit.com
127.0.0.1  www.the-exit.com
127.0.0.1  toteen.com #[Trojan.Bookmarker.G]
127.0.0.1  out.true-counter.com #[Trojan.Bootconf][CWS.Msinfo]
127.0.0.1  true-counter.com #[Trojan.Slog]
127.0.0.1  www.true-counter.com
127.0.0.1  warlog.info #[server down?]
127.0.0.1  winbabes.com #[IFrame.Exploit]
127.0.0.1  yellow-pages.ws #[searchmeup.com]
127.0.0.1  search.yellow-pages.ws
127.0.0.1  yoursearch.ws
# [game4all.biz Group][Vasiliy Ivanov][Vx.Cactus]
127.0.0.1  3xcash.biz
127.0.0.1  3xvideogalleries.com #[server down.all]
127.0.0.1  gaystogay.com
127.0.0.1  www.gaystogay.com
# [Danyelle Christian]
127.0.0.1  realsearch.cc #[Trojan.RealSearch]
# [Conyc][Searchportal]
127.0.0.1  krutahuli.info
127.0.0.1  search-daily.com #[TROJ_CLICKER.E]
127.0.0.1  www.search-daily.com
# [DeAngelo Saint][Ivanenko Sergey][Dimon Server]
127.0.0.1  4click.biz
127.0.0.1  targetsearch.info #[Trojan.StartPage.H]
127.0.0.1  v-nature.biz #[MHTMLRedir.Exploit]
# [FlatHousing-Group][makeat.net]
127.0.0.1  congar.biz
127.0.0.1  www.ddload.net
127.0.0.1  edonkey2000.at
127.0.0.1  snipernet.biz
127.0.0.1  snipernet.us #[MHTMLRedir.Exploit][paretologic.com]
127.0.0.1  sxload.com #[Win32/TrojanDownloader.VB.KA]
127.0.0.1  bar.sxload.com #[MHTMLRedir.Exploit]
127.0.0.1  www.sxload.com
# [Galina Charmandjieva]
127.0.0.1  count.cc #[TROJ_STRTPAG.AC][TROJ_STARTPAG.AG]
127.0.0.1  js.count.cc
127.0.0.1  ewizard.cc #[Troj/AdClick-AH][TROJ_STARTPAG.LC]
127.0.0.1  c1dcon.ewizard.cc
127.0.0.1  cldcon.ewizard.cc
127.0.0.1  s12ds1.ewizard.cc #[Win32.Startpage.NS]
127.0.0.1  s13ds.ewizard.cc
127.0.0.1  s1di.ewizard.cc
# [ICommerce Solutions][MK Digital Media][IMPRO CORPORATION]
127.0.0.1  becomers.com
127.0.0.1  imgs.becomers.com
127.0.0.1  www.becomers.com
127.0.0.1  cameup.com #[MHTMLRedir.Exploit]
127.0.0.1  www.cameup.com
127.0.0.1  drugwebsearch.com
127.0.0.1  www.digimedia.com #[Wishbone.com]
127.0.0.1  ez-finder.com #[Win32/TrojanDownloader.Small.AZG]
127.0.0.1  www.ez-finder.com
127.0.0.1  find-help.org #[McAfee.Adware-Tolbar.dll]
127.0.0.1  www.find-help.org
127.0.0.1  gosrch.info #[Spamdexing]
127.0.0.1  icommerce.ws #[Malicious.Links]
127.0.0.1  www.icommerce.ws #[MHTMLRedir.Exploit]
127.0.0.1  intelligence-search.com
127.0.0.1  imgs.itsoktosearch.net
127.0.0.1  www.itsoktosearch.net #[klikfind.com]
127.0.0.1  iwantsearch.com #[TROJ_AGENT.EX][SPYW_STARTPAGE.A]
127.0.0.1  www.iwantsearch.com #[Adware.Iwantsearch]
127.0.0.1  www.klikcash.com
127.0.0.1  klikdomains.com
127.0.0.1  www.klikdomains.com
127.0.0.1  klikfind.com #[PcTools.Klikfind]
127.0.0.1  imgs.klikfind.com #[McAfee.Adware-Click]
127.0.0.1  www.klikfind.com
127.0.0.1  www.kliksearch.com #[CWS.Aff.Toolband]
127.0.0.1  klikvipsearch.com
127.0.0.1  www.klikvipsearch.com #[Spamdexing]
127.0.0.1  www.mk-digital.com
127.0.0.1  northvip.com #[Spamdexing]
127.0.0.1  qooqqle.com
127.0.0.1  www.qooqqle.com
127.0.0.1  satiristlist.com
127.0.0.1  searchservices.info
127.0.0.1  www.searchservices.info
127.0.0.1  spycut.com #[Rogue/Suspect][SiteAdvisor.spycut.com]
127.0.0.1  get.spycut.com
127.0.0.1  help.spycut.com
127.0.0.1  support.spycut.com
127.0.0.1  www.spycut.com #[Webhelper.CWS List]
127.0.0.1  superadultsearch.com #[Spamdexing][server down?]
127.0.0.1  www.superadultsearch.com
127.0.0.1  ultra-porn.biz #[Google.Warning]
127.0.0.1  www.ultra-porn.biz
127.0.0.1  web--search.com #[McAfee.Adware-SBSoft]
127.0.0.1  www.web--search.com
127.0.0.1  yeahsearch.net
127.0.0.1  www.yeahsearch.net
# [Independet]
127.0.0.1  600pics.com
127.0.0.1  www.600pics.com #[Panda.SpamNet.A]
127.0.0.1  all-tgp.org
127.0.0.1  www.all-tgp.org
127.0.0.1  extratgp.com
127.0.0.1  www.hotseriesmix.com
127.0.0.1  hqthumbz.com
127.0.0.1  www.onlyhotlinks.com #[Webhelper.CWS List]
127.0.0.1  picslab.com
127.0.0.1  www.picslab.com
127.0.0.1  sex-pics.biz
127.0.0.1  traf-monitor.com
127.0.0.1  traf-sale.com
# [InterWeb Solutions][Coolwebsearch Group]
127.0.0.1  coolwebsearch.com #[Trojan.TrustedZones]
127.0.0.1  php.coolwebsearch.com
127.0.0.1  search_fd.php.coolwebsearch.com #[Wildcard DNS]
127.0.0.1  stats.coolwebsearch.com
127.0.0.1  www.coolwebsearch.com #[CWS/IEFeats]
127.0.0.1  searchanyway.com
127.0.0.1  feed.searchanyway.com #[coolwebsearch.com]
127.0.0.1  go.searchanyway.com
127.0.0.1  www.searchanyway.com
# [Javon Lockley]
127.0.0.1  buy-traffic.net #[searchmeup.com]
127.0.0.1  ibuytraffic.net
# [JRC Group][Anchor Group Ltd][IDEASFORHOST.COM]
127.0.0.1  www.adult-dvdmovie.com #[JS/Relink-B][JS_RELINK.A]
127.0.0.1  e-finder.cc
127.0.0.1  www.e-finder.cc #[CWS.Addclass.2][StartPage-DA]
127.0.0.1  eager-search.cc
127.0.0.1  ehttp.cc #[CWS.Addclass][TROJ_STARTPAGE.D][Spyware.CWSAddClass]
127.0.0.1  fast-look.com
127.0.0.1  www.fast-look.com
127.0.0.1  www.lucky-finder.com
127.0.0.1  rightfinder.net #[CWS.Addclass.2]
127.0.0.1  www.rightfinder.net #[Troj/StartPg-AY]
127.0.0.1  securitycenter.cc #[Trojan.StartPage.K]
127.0.0.1  www.securitycenter.cc
127.0.0.1  spyware-locator.cc
127.0.0.1  www.spyware-locator.cc
127.0.0.1  swift-look.com #[phishing exploit]
127.0.0.1  www.swift-look.com
127.0.0.1  tadstore.cc #[CWS.Addclass.2][rightfinder.net]
127.0.0.1  webcruiser.cc #[TROJ_SMALL.AFG]
127.0.0.1  www.webcruiser.cc #[Trojan.Startpage.O]
# [Pan Koudelka Group]
127.0.0.1  aflcub.t.muxa.cc #[Wildcard DNS]
127.0.0.1  bjvvhk.t.muxa.cc #[Adware.Raxums]
127.0.0.1  cpzlcc.t.muxa.cc
127.0.0.1  fzkdvi.t.muxa.cc
127.0.0.1  mzyzlu.t.muxa.cc #[Troj/StartPa-CB]
127.0.0.1  pcwlrh.t.muxa.cc #[REG_STARTPAGE.R]
127.0.0.1  ujrodh.t.muxa.cc
127.0.0.1  bin.wordsx.cc #[TROJ_SAMLLAMB.A]
# [Rasta Community][Wildcard DNS]
127.0.0.1  nakurka.org
127.0.0.1  search.smokaz.com
# [Irgi Magel][Stanislav Avdeiko]
127.0.0.1  cc20foreva.com
127.0.0.1  greg-tut.com #[MHTMLRedir.Exploit]
127.0.0.1  hardcoreover.com
127.0.0.1  master-se.com
127.0.0.1  mig29here.com #[PWSteal.Revcuss.C]
127.0.0.1  sexclon.com #[SiteAdvisor.sexclon.com]
127.0.0.1  thestas.com #[Downloader-OT][TROJ_SMALL.ZY]
127.0.0.1  win-eto.com #[TROJ_PUPER.AT][Wildcard DNS]
127.0.0.1  0.win-eto.com
# [Networld One][Enternet Media]
127.0.0.1  www.1800searchonline.com
127.0.0.1  www.1stsearchportal.com
127.0.0.1  www.21andover.com
127.0.0.1  www.24-7searching-and-more.com
127.0.0.1  www.971searchbox.com
127.0.0.1  aaawebfinder.com
127.0.0.1  www.ampmsearch.com
127.0.0.1  audioseek.net
127.0.0.1  music-downloads.audioseek.net
127.0.0.1  www.audioseek.net
127.0.0.1  c4tdownload.com #[Trojan.TrustedZones]
127.0.0.1  ptp.c4tdownload.com #[Adware.ClickDLoader.B]
127.0.0.1  www.clickhere4search.com
127.0.0.1  www.clicktomakeasearch.com
127.0.0.1  www.directsearchzone.com
127.0.0.1  easysearch4you.com
127.0.0.1  www.easysearch4you.com #[F-Secure.EliteBar.A]
127.0.0.1  virt0.enternetmedia.com
127.0.0.1  www.enternetmedia.com
127.0.0.1  www.enterthesearch.com
127.0.0.1  www.esearch2005.com
127.0.0.1  www.esearchnation.com
127.0.0.1  eza1netsearch.com #[FaceTime.W32/Sdbot-ADD]
127.0.0.1  www.eza1netsearch.com #[searchmiracle.com]
127.0.0.1  www.ezwebsearching.com
127.0.0.1  www.freestuffengine.com
127.0.0.1  www.globalefinder.com
127.0.0.1  www.go2realsearch.com
127.0.0.1  hangoutspot.com
127.0.0.1  www.hangoutspot.com
127.0.0.1  www.myseachexplorer.com
127.0.0.1  perinstall.com
127.0.0.1  www.pcmonitorpro.com
127.0.0.1  www.quicksearch360.com
127.0.0.1  www.quickvitamins.net
127.0.0.1  www.s1s1s1search.com
127.0.0.1  www.search101online.com
127.0.0.1  www.search123forme.com
127.0.0.1  www.search345quest.com
127.0.0.1  searchmiracle.com #[Adware.EliteBar.B][Trojan.StartPage.NK]
127.0.0.1  ad1.searchmiracle.com
127.0.0.1  ads1.searchmiracle.com #[Wildcard DNS]
127.0.0.1  bobby.searchmiracle.com
127.0.0.1  infoget.searchmiracle.com
127.0.0.1  install.searchmiracle.com #[TROJ_LOWZONES.H][ADW_ELITE.A]
127.0.0.1  install23.searchmiracle.com
127.0.0.1  install30.searchmiracle.com #[AdClicker-BA]
127.0.0.1  641.searchmiracle.com
127.0.0.1  10016.searchmiracle.com #[SiteAdvisor.searchmiracle.com]
127.0.0.1  9310.searchmiracle.com
127.0.0.1  u.searchmiracle.com
127.0.0.1  update32.searchmiracle.com
127.0.0.1  www.searchmiracle.com #[Trojan.EliteBar][Trojan.TrustedZone]
127.0.0.1  www.searchtheworld4you.com
127.0.0.1  www.searchwebzone.com
127.0.0.1  www.seektheglobe.com
127.0.0.1  sitesearchcentral.com
127.0.0.1  www.sitesearchcentral.com
127.0.0.1  in.spywarebomber.com
127.0.0.1  www.spywarebomber.com #[Rogue/Suspect]
127.0.0.1  therealsearch.com #[CWS.Therealsearch]
127.0.0.1  conf.therealsearch.com
127.0.0.1  www.therealsearch.com #[Trojan.Realsrch.A]
127.0.0.1  www.the818search-co.com
127.0.0.1  www.type2find.com
127.0.0.1  websoftsecure.com #[Rogue/Suspect]
127.0.0.1  www.websoftsecure.com
127.0.0.1  www.xosearchox.com
127.0.0.1  www.yoursearchspace.com
127.0.0.1  yupsearch.com #[McAfee.Adware-EliteBar.dll]
127.0.0.1  install38.yupsearch.com #[Trojan.StartPage.NK]
127.0.0.1  update.yupsearch.com #[Wildcard DNS][Win32/TrojanDropper.Agent.TV]
127.0.0.1  www.yupsearch.com
# [New Access Ltd]
127.0.0.1  www.contentcooler.biz #[Trojan.TrustedZone][Kephyr.PUP]
127.0.0.1  new-access.biz #[SiteAdvisor.new-access.biz]
127.0.0.1  www.new-access.biz #[Trojan.TrustedZone]
# [Hassan Pennock]
127.0.0.1  00hq.com #[Adware.Winshow]
127.0.0.1  www.00hq.com
127.0.0.1  75tz.com #[Win32.Winshow.G][Troj/Dloader-KS]
127.0.0.1  www.75tz.com
127.0.0.1  adasearch.com
127.0.0.1  www.adasearch.com #[Hayter Merchants Group]
127.0.0.1  easysearchingtips.com #[somesearch.net]
127.0.0.1  www.engine-to-search.com
127.0.0.1  enjoywebsurf.com
127.0.0.1  www.enjoywebsurf.com
127.0.0.1  www.findabouteverything.com
127.0.0.1  www.findinnet.com
127.0.0.1  fine-search.net
127.0.0.1  www.fine-search.net
127.0.0.1  full-search.net
127.0.0.1  go2-search.com
127.0.0.1  iefeadsl.com #[Win32.Winshow.G][Adware.CWSIEFeats]
127.0.0.1  www.iefeadsl.com
127.0.0.1  onemoresearch.net
127.0.0.1  www.onemoresearch.net
127.0.0.1  rf104.com #[iefeadsl.com][Troj/Dloader-KS]
127.0.0.1  search-777.com
127.0.0.1  search-all-fast.com #[Win32.Winshow.N]
127.0.0.1  search-to-find.com
127.0.0.1  search-motor.com
127.0.0.1  www.search-motor.com
127.0.0.1  www.search-what.net
127.0.0.1  www.searchinwww.com
127.0.0.1  www.searchwhatuwant.com
127.0.0.1  totalsearches.com #[McAfee.Adware-WinShow]
127.0.0.1  www.totalsearches.com
127.0.0.1  www.websearchplace.com
# [Pavel Petroff]
127.0.0.1  www.buckstoolbar.com
127.0.0.1  www.licksex.com #[Hayter Merchants Group]
127.0.0.1  www.mpegs4sex.com #[Hayter Merchants Group]
127.0.0.1  www.typeintofind.com #[search-to-find.com]
127.0.0.1  www.umaxpartner.com
127.0.0.1  veryeasysearch.com #[coolsearchengine.net]
127.0.0.1  www.veryeasysearch.com #[McAfee.QlowZones-25]
127.0.0.1  counter.xxxcool.com
127.0.0.1  xxxcool.com #[gpisoft.com][Hayter Merchants Group]
# [Ross Morriss][DMC MEDIA GROUP]
127.0.0.1  1-se.com #[CWS.Aboutblank][W32.Tuoba.Trojan]
127.0.0.1  www.1-se.com #[VBS.Startpage.C]
127.0.0.1  ie-search.com #[CWS.Loadbat][umaxsearch.com]
127.0.0.1  www.ie-search.com
127.0.0.1  search-ing.com
127.0.0.1  www.search-ing.com
127.0.0.1  findloss.com #[umaxsearch.com]
127.0.0.1  www.findloss.com
# [Search Media Int]
127.0.0.1  bestwebsearch.org
127.0.0.1  catalog.bestwebsearch.org
127.0.0.1  www.bestwebsearch.org #[AVG.Startpage.HG]
# [UmaxSearch Ltd Group][Leos Rousek]
127.0.0.1  www.lookuplive.com
127.0.0.1  www.payse.com
127.0.0.1  payse.net
127.0.0.1  paysefeed.net
127.0.0.1  searchadv.com
127.0.0.1  www.searchadv.com #[Spamdexing]
127.0.0.1  searchmeup.com #[CWS.Svcinit.3]
127.0.0.1  www.searchmeup.com #[SunBelt.SearchMeUp Hijacker]
127.0.0.1  topadult10.com
127.0.0.1  www.topadult10.com
127.0.0.1  www.topauto10.com #[Spamdexing][Microsoft.Strider]
127.0.0.1  topcasino10.com
127.0.0.1  www.topcasino10.com
127.0.0.1  topmeds10.com
127.0.0.1  www.topmeds10.com
127.0.0.1  www.topmobile10.com
127.0.0.1  www.topsearch10.com #[Spamdexing]
127.0.0.1  www.toptravel10.com
127.0.0.1  xml.umaxfeed.com
127.0.0.1  www.umaxlogin.com
127.0.0.1  umaxsearch.com #[TROJ_ESEPOR.A][CWS.Xplugin]
127.0.0.1  www.umaxsearch.com #[Adware.Umaxsearch]
# [Vasia Pupkin]
127.0.0.1  rapefreepics.com
127.0.0.1  www.rapefreepics.com
127.0.0.1  prolivation.com
127.0.0.1  www.prolivation.com
127.0.0.1  sexyque.com #[SunBelt.Sexyque.com]
127.0.0.1  www.sexyque.com
# [VladZone][Vlad][Spaceland Arcade][JpS Projects][John Ship]
127.0.0.1  about-blank.biz
127.0.0.1  home.about-blank.biz #[panet.org]
127.0.0.1  altblue.org
127.0.0.1  www.altblue.org
127.0.0.1  www.awmdev.com
127.0.0.1  www.centropachamama.com
127.0.0.1  c.clickaire.com
127.0.0.1  www.forexcredit.com
127.0.0.1  idgsearch.com #[GoogleMS Search Helper][CWS.Googlems]
127.0.0.1  www.idgsearch.com #[Trojan.Digits][Wildcard DNS]
127.0.0.1  www.jps.ms
127.0.0.1  jps.ru
127.0.0.1  images.jps.ru
127.0.0.1  www.jps.ru #[adslim.com]
127.0.0.1  www.lavasoft-spyware.com
127.0.0.1  www.modget.com
127.0.0.1  www.mohaabh.com
127.0.0.1  download.moonri.com
127.0.0.1  ras.moonri.com #[Win32/TrojanDownloader.IstBar.EQ]
127.0.0.1  www.moonri.com
127.0.0.1  www.sebot.biz
127.0.0.1  www.seohit.biz
127.0.0.1  www.seohit.com
127.0.0.1  www.seawrold.org
127.0.0.1  slimcash.biz #[slimcash.com]
127.0.0.1  www.smslive.ru
127.0.0.1  www.starimaribor.com
127.0.0.1  tramadolphentermine.info #[c.slimppc.com]
127.0.0.1  vladzone.com #[Trojan.TrustedZone]
127.0.0.1  download.vladzone.com #[TROJ_SMALL.LY][win32/TrojanClicker.Agent.BF]
127.0.0.1  toolbar.vladzone.com #[MHTMLRedir.Exploit]
127.0.0.1  www.vladzone.com #[TrojanDropper.Win32.Small.cw]
127.0.0.1  www.weddle.ru
127.0.0.1  xibu315.com
# [JpS Group via Absolutee Corp]
127.0.0.1  ad.adslim.com #[Win32.Slimad.C]
127.0.0.1  www.adslim.com #[Panda.Spyware.Slimield]
127.0.0.1  e.attrezzi.biz #[EXP/MS05-002.Ani.A]
127.0.0.1  ad.eltext.com #[eTrust.Win32/Beenut]
127.0.0.1  www.fet2cash.com
127.0.0.1  www.impotato.com #[Trojan.Win32.Dialer.oy]
127.0.0.1  c.imputati.com #[Trojan.Win32.Agent.qt]
127.0.0.1  installare.net #[Win32/Dialer.OY]
127.0.0.1  code.jcash.biz
127.0.0.1  img.jcash.biz
127.0.0.1  content.jdial.biz #[Trojan.Nebuler][Win32/Dialer.PornDial.F]
127.0.0.1  www.jdial.biz
127.0.0.1  d.mettere.net #[Win32/Dialer.QS]
127.0.0.1  mezzicodec.net
127.0.0.1  www.mezzicodec.net
127.0.0.1  www.pornohome.net
127.0.0.1  search--control.com #[eTrust.SlimSearch]
127.0.0.1  www.search--control.com
127.0.0.1  slimcash.com
127.0.0.1  www.slimcash.com
127.0.0.1  slimfind.com #[eTrust.SlimSearch]
127.0.0.1  webalizer.slimfind.com
127.0.0.1  www.slimfind.com #[c.slimppc.com]
127.0.0.1  c.slimppc.com
127.0.0.1  www.slimppc.com
127.0.0.1  slimshield.com #[Rogue/Suspect]
127.0.0.1  www.slimshield.com #[SiteAdvisor.slimshield.com]
127.0.0.1  slimtoolbar.com #[AdWare.Win32.Softomate.k]
127.0.0.1  www.slimtoolbar.com
127.0.0.1  download.spyware-wiper.com
127.0.0.1  www.spyware-wiper.com #[Rogue/Suspect]
127.0.0.1  web.webforhumans.com
127.0.0.1  www.webforhumans.com
127.0.0.1  secure.widebill.com
# [Look2Me via Absolutee Corp][Arizonaenterprisesllc.com]
127.0.0.1  inte-rnet.com
127.0.0.1  onli-ne.com
127.0.0.1  vvv.onli-ne.com
127.0.0.1  www.onli-ne.com #[TR/Dldr.Adload.FV]
127.0.0.1  www.searc-h.com
# [Various via Absolutee Corp]
127.0.0.1  clickpeak.net
127.0.0.1  iframebiz.com #[Backdoor.Mydopam]
# [Sid Wongvorakul][Dmitriy Soldatenko]
127.0.0.1  baikal-guide.com #[SiteAdvisor.baikal-guide.com]
127.0.0.1  www.domains-parking.com
127.0.0.1  dimattic.com #[HTML/Exploit.VMLFill]
127.0.0.1  www.dimattic.com
127.0.0.1  dsdomain.com
127.0.0.1  qoclick.com #[HTML/Exploit.VMLFill]
127.0.0.1  color-contacts.seohuntress.com #[HTML/Exploit.VMLFill]
127.0.0.1  www.seohuntress.com #[qoclick.com]
127.0.0.1  specific911.biz
127.0.0.1  www.specific911.biz
127.0.0.1  specific911.net #[SunBelt.Specific911]
127.0.0.1  www.specific911.net
127.0.0.1  specific911.org
127.0.0.1  www.specific911.org
127.0.0.1  pay-per-search.weekly-pay.com #[Win32/Delf.NCD]
# [Olaf Yohansen][First Aid][Troj/IEStart-F]
127.0.0.1  opsex.com
127.0.0.1  www.opsex.com
127.0.0.1  winshow.biz
127.0.0.1  www.winshow.biz
# [End of CWS Affiliates]
#
# [Cyberware LTD][Parasite.SVAPlayer]
127.0.0.1  internetwasher.com
127.0.0.1  alerts.internetwasher.com #[a349.g.akamai.net]
127.0.0.1  download.internetwasher.com
127.0.0.1  www.internetwasher.com
127.0.0.1  popupblockade.com #[Parasite.Httper]
127.0.0.1  www.popupblockade.com
127.0.0.1  systemsoap.com #[Parasite.Zipclix and Httper]
127.0.0.1  alerts.systemsoap.com #[a536.g.akamai.net]
127.0.0.1  secure.systemsoap.com
127.0.0.1  www.systemsoap.com
127.0.0.1  ba2.systemsoap.net
127.0.0.1  secure.systemsoap.net
127.0.0.1  config.url404.com #[Parasite.Httper][a1719.g.akamai.net]
# [Cyberheat, Inc]
127.0.0.1  www.adwareremovergold.com #[Rogue/Suspect]
127.0.0.1  ares.chinoc.net
127.0.0.1  chinoc.net
127.0.0.1  dev138.chinoc.net
127.0.0.1  j5.chinoc.net
127.0.0.1  kw15.chinoc.net
127.0.0.1  kw17.chinoc.net
127.0.0.1  kw29.chinoc.net
127.0.0.1  kw40.chinoc.net
127.0.0.1  kw46.chinoc.net
127.0.0.1  kw62.chinoc.net
127.0.0.1  kw79.chinoc.net
127.0.0.1  kw80.chinoc.net
127.0.0.1  kw82.chinoc.net
127.0.0.1  kw83.chinoc.net
127.0.0.1  kw85.chinoc.net
127.0.0.1  kw107.chinoc.net
127.0.0.1  kw122.chinoc.net
127.0.0.1  kw123.chinoc.net
127.0.0.1  v5.chinoc.net
127.0.0.1  www.clients-support.com
127.0.0.1  os.cyberheatinc.com
127.0.0.1  www.datashreddergold.com
127.0.0.1  iblockpopups.com #[SiteAdvisor.iblockpopups.com]
127.0.0.1  www.iblockpopups.com #[ZeroPopUpBar]
127.0.0.1  iquicksearch.com #[eTrust.IQuickSearch]
127.0.0.1  www.iquicksearch.com
127.0.0.1  members-access.com
127.0.0.1  www.movieaccess.com
127.0.0.1  www.pcspeedbooster.com #[TheWatcher List]
127.0.0.1  www.searchbuckz.com
127.0.0.1  seekio.com
127.0.0.1  sureseeker.com #[JS.Trojan.Seeker.b]
127.0.0.1  www.sureseeker.com
127.0.0.1  botw.topbucks.com
127.0.0.1  cluster-03.topbucks.com
127.0.0.1  mainstream.topbucks.com
127.0.0.1  rainbow.topbucks.com
127.0.0.1  referral.topbucks.com
127.0.0.1  vod.topbucks.com
127.0.0.1  referral.vod.topbucks.com
127.0.0.1  www.topbucks.com
127.0.0.1  www.topcash.com
127.0.0.1  twink4cash.com
127.0.0.1  www.twinkforcash.com
127.0.0.1  www.twinksforcash.com
# [Cybernet Quest]
127.0.0.1  cqcounter.com #[SecuritySpace.WebBug]
127.0.0.1  img.cqcounter.com
127.0.0.1  nl.cqcounter.com
127.0.0.1  no.2.cqcounter.com
127.0.0.1  se.cqcounter.com
127.0.0.1  xxx.cqcounter.com
127.0.0.1  zz.cqcounter.com
127.0.0.1  ar.2.cqcounter.com
127.0.0.1  au.2.cqcounter.com
127.0.0.1  bg.2.cqcounter.com
127.0.0.1  ca.2.cqcounter.com
127.0.0.1  de.2.cqcounter.com
127.0.0.1  fr.2.cqcounter.com
127.0.0.1  nz.2.cqcounter.com
127.0.0.1  si.2.cqcounter.com
127.0.0.1  th.2.cqcounter.com
127.0.0.1  uk.2.cqcounter.com
127.0.0.1  us.2.cqcounter.com #[Wildcard DNS]
127.0.0.1  us.cqcounter.com
127.0.0.1  1au.cqcounter.com
127.0.0.1  1bm.cqcounter.com
127.0.0.1  1ca.cqcounter.com
127.0.0.1  1de.cqcounter.com
127.0.0.1  1es.cqcounter.com
127.0.0.1  1fr.cqcounter.com
127.0.0.1  1in.cqcounter.com
127.0.0.1  1it.cqcounter.com
127.0.0.1  1jo.cqcounter.com
127.0.0.1  1nl.cqcounter.com
127.0.0.1  1pt.cqcounter.com
127.0.0.1  1se.cqcounter.com
127.0.0.1  1th.cqcounter.com
127.0.0.1  1ua.cqcounter.com
127.0.0.1  1uk.cqcounter.com
127.0.0.1  1us.cqcounter.com
127.0.0.1  1xxx.cqcounter.com
127.0.0.1  www2.cqcounter.com
127.0.0.1  www.cqcounter.com
127.0.0.1  counter.w3open.com
127.0.0.1  ns2.w3open.com
# [Cydoor Technologies][Online Media Solutions]
127.0.0.1  jcontent.bns1.net
127.0.0.1  www.bns1.net #[Kaspersky.Adware.Cydoor]
127.0.0.1  www.bns2.net
127.0.0.1  cjt1.net
127.0.0.1  j800banners.cjt1.net
127.0.0.1  jadlogix.cjt1.net
127.0.0.1  jadtegrity.cjt1.net
127.0.0.1  jadvernet.cjt1.net
127.0.0.1  jaimmedia.cjt1.net
127.0.0.1  javatar.cjt1.net
127.0.0.1  jbeet.cjt1.net
127.0.0.1  jbigpops.cjt1.net
127.0.0.1  jbravenet.cjt1.net
127.0.0.1  jcdcover.cjt1.net
127.0.0.1  jclickspring.cjt1.net
127.0.0.1  jcollegehumor.cjt1.net
127.0.0.1  jdownloadacc.cjt1.net
127.0.0.1  jdownloadaccint.cjt1.net
127.0.0.1  jedonkey.cjt1.net
127.0.0.1  jeuniverse.cjt1.net
127.0.0.1  jgen4.cjt1.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  jgen44.cjt1.net
127.0.0.1  jgen55.cjt1.net
127.0.0.1  jhot.cjt1.net
127.0.0.1  jicmedia.cjt1.net
127.0.0.1  jicq.cjt1.net
127.0.0.1  jieplugin.cjt1.net
127.0.0.1  jinternetoptimizer.cjt1.net
127.0.0.1  jmamma.cjt1.net
127.0.0.1  jmbi31.cjt1.net
127.0.0.1  jmediabuy1.cjt1.net
127.0.0.1  jmediabuyad.cjt1.net
127.0.0.1  jmindset.cjt1.net
127.0.0.1  jmindsettest.cjt1.net
127.0.0.1  jmpeg.cjt1.net
127.0.0.1  jnictech.cjt1.net
127.0.0.1  jpalt.cjt1.net
127.0.0.1  jpiolet.cjt1.net
127.0.0.1  jsanboxer.cjt1.net
127.0.0.1  jseedcorn.cjt1.net
127.0.0.1  jsercee.cjt1.net
127.0.0.1  jthedelfin.cjt1.net
127.0.0.1  jwarezp2p.cjt1.net
127.0.0.1  jwildmedia.cjt1.net
127.0.0.1  jwindsorandpearl.cjt1.net
127.0.0.1  mediabuy-nic.cjt1.net
127.0.0.1  oascentral.cjt1.net #[RealMedia]
127.0.0.1  j.2004cms.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  cydoor.com #[SiteAdvisor.cydoor.com]
127.0.0.1  ct.cydoor.com
127.0.0.1  redirect.cydoor.com
127.0.0.1  www.cydoor.com #[Adware.Cydoor][SunBelt.Cydoor.com]
# [Daisycon]
127.0.0.1  affiliates.kliks.nl
127.0.0.1  servlets.kliks.nl
127.0.0.1  www1.kliks.nl
127.0.0.1  www2.kliks.nl
127.0.0.1  www.kliks.nl
127.0.0.1  popupmoney.com
127.0.0.1  server01.popupmoney.com
127.0.0.1  www.popupmoney.com
# [Da Hang Ji Ye]
127.0.0.1  0ml.net
127.0.0.1  b0o.net
# [D&D Internet Services]
127.0.0.1  cluster.blingblingcontent.com
127.0.0.1  gb.blingblingcontent.com
127.0.0.1  s7.blingblingcontent.com #[HJTH.EasyWebSearch Hijacker]
127.0.0.1  www.e-sexcash.com
127.0.0.1  www.easywebsearch.nl #[Easywebinstaller Control][server down.all]
127.0.0.1  www.waypointcash.com
# [Deloitte corp][Greg McLohkil][Andrzej Zborowski]
127.0.0.1  js.pceb.cc #[Trojan.Win32.Rootkit.E]
# [Dmitriy Gerasimov]
127.0.0.1  www.dimkus.com
127.0.0.1  info.mytrix.cz #[Wildcard DNS]
127.0.0.1  stats.mytrix.cz
127.0.0.1  www.mytrix.cz #[SPYW_MORWILBAR.A]
127.0.0.1  www.netcross.cz #[Adware.MWSearch][SiteAdvisor.netcross.cz]
127.0.0.1  www.netcross.info #[SPYW_MORWILBAR.A]
127.0.0.1  www.pragueline.com #[coolwebsearch.com]
127.0.0.1  www.webseek.cz
127.0.0.1  ya.cz
# [DigitalNames]
127.0.0.1  digitalnames.net
127.0.0.1  dnplugin.digitalnames.net #[Spyware.DigitalNames]
127.0.0.1  download.digitalnames.net
127.0.0.1  hanafos.digitalnames.net
127.0.0.1  search.digitalnames.net
127.0.0.1  service.digitalnames.net
127.0.0.1  service1.digitalnames.net
127.0.0.1  service2.digitalnames.net
127.0.0.1  service3.digitalnames.net
127.0.0.1  update.digitalnames.net #[SPYW_DIGITALNM.A]
127.0.0.1  upgrade.digitalnames.net #[AdWare.DigitalNames.g]
127.0.0.1  www.digitalnames.net #[McAfee.Adware-DigitalNames]
# [Digital River][Direct Response Technologies]
127.0.0.1  affiliates.adfinity.com #[adfinity.wip.directresponsetech.com]
127.0.0.1  clickauditor.net
127.0.0.1  affiliates.copeac.com #[intermarkmedia.wip.directresponsetech.com]
127.0.0.1  directcoupons.com
127.0.0.1  directleads.com #[Whois.Blacklisted]
127.0.0.1  directtrack.com
127.0.0.1  adultadworld.directtrack.com
127.0.0.1  bingorevenue.directtrack.com
127.0.0.1  cpacampaigns.directtrack.com
127.0.0.1  doubleyourdating.directtrack.com
127.0.0.1  gozing.directtrack.com
127.0.0.1  images.directtrack.com
127.0.0.1  imagecache.directtrack.com
127.0.0.1  img.directtrack.com
127.0.0.1  latin3.directtrack.com
127.0.0.1  niteflirt.directtrack.com
127.0.0.1  offersquest.directtrack.com
127.0.0.1  rapidresponse.directtrack.com #[SpySweeper.Spy.Cookie]
127.0.0.1  revenuegateway.directtrack.com
127.0.0.1  secure.directtrack.com #[SpySweeper.Spy.Cookie]
127.0.0.1  sideshow.directtrack.com
127.0.0.1  trafficneeds.directtrack.com
127.0.0.1  varsityads.directtrack.com #[MVPS.Criteria]
127.0.0.1  www.directtrack.com
127.0.0.1  eajmp.com
127.0.0.1  www.eajmp.com #[MVPS.Criteria]
127.0.0.1  ad1.gamezone.com #[RealMedia]
127.0.0.1  keywordmax.com
127.0.0.1  www.keywordmax.com
# [Direct Information Group][Parking Service]
127.0.0.1  parking.ad3.com
127.0.0.1  images.bmnq.com
127.0.0.1  images.cnomy.com
127.0.0.1  pics.cnomy.com
127.0.0.1  images.skenzo.com
127.0.0.1  img.skenzo.com
127.0.0.1  pics.skenzo.com
127.0.0.1  www.theuniquesearch.com
127.0.0.1  ads.webhosting.info
# [Domain Deluxe][Hitfarm Group][Parking Service]
127.0.0.1  cluster1.hitfarm.com
127.0.0.1  landing.hitfarm.com
127.0.0.1  static.hitfarm.com
# [Domain Escrow Services][Carmen Media Group]
127.0.0.1  clickedyclick.com #[McAfee.Cookie-Clickedyclick]
127.0.0.1  www.clickedyclick.com #[SunBelt.ClickedyClick]
# ["Domains by Proxy"]
127.0.0.1  ad-clix.com
127.0.0.1  www.ad-clix.com
127.0.0.1  www.contextpanel.com #[searchant.com]
127.0.0.1  searchant.com #[SunBelt.saSyncMgr]
127.0.0.1  www.searchant.com
127.0.0.1  searchingall.com #[AdWare.Kodpye.a]
127.0.0.1  www.searchingall.com
127.0.0.1  www.searchmain.com #[Adware.CSearch]
127.0.0.1  seekseek.com #[ADW_SCANPORTAL.A][Adware.SeekSeek]
127.0.0.1  www.seekseek.com #[Troj/StartPa-MP][Spyware.Seekseek]
127.0.0.1  superwebsearch.com #[Parasite.ILookup][Adware.ILookup]
127.0.0.1  www.superwebsearch.com
# [Domains by Proxy via NavExcel Group]
127.0.0.1  navexcel.com #[eTrust.NavExcel][Adware.NavHelper]
127.0.0.1  www.navexcel.com #[SiteAdvisor.navexcel.com]
127.0.0.1  www.trustedsearch.com #[eTrust.Navexcel]
# [DomainSpa LLC][Parking Service]
127.0.0.1  domainsspa.com #[WIPO.D2006-0523]
127.0.0.1  www.domainsspa.com #[Whios.Blacklisted]
127.0.0.1  hus.parkingspa.com #[Microsoft.Typo-Patrol]
127.0.0.1  zoo.parkingspa.com
127.0.0.1  zoo-a.parkingspa.com
# [Doteasy Technology][Hitstation Communication]
127.0.0.1  adserve.doteasy.com
127.0.0.1  pbg2cs01.doteasy.com
127.0.0.1  hitcounter01.xspp.com
# [Doubleclick][Tracking Service]
127.0.0.1  eqchmdnvip1.2mdn.net #[SiteAdvisor.zapspot]
127.0.0.1  m.2mdn.net
127.0.0.1  m1.au.2mdn.net
127.0.0.1  m1.2mdn.net #[a509.cd.akamai.net]
127.0.0.1  m2.2mdn.net
127.0.0.1  m.uk.2mdn.net
127.0.0.1  twx.2mdn.net #[server down?]
127.0.0.1  n339.asp-cc.com
127.0.0.1  cc-dt.com
127.0.0.1  ads.cc-dt.com
127.0.0.1  clickserve.cc-dt.com
127.0.0.1  creative.cc-dt.com
127.0.0.1  clickserve.dartsearch.net
127.0.0.1  clickserve.eu.dartsearch.net
127.0.0.1  clickserve.uk.dartsearch.net
127.0.0.1  doubleclick.net #[McAfee.Cookie-Doubleclick]
127.0.0.1  ad.doubleclick.net #[MVPS.Criteria]
127.0.0.1  ad2.doubleclick.net #[Panda.Spyware:Cookie/Doubleclick]
127.0.0.1  ad.3ad.doubleclick.net
127.0.0.1  ad.3au.doubleclick.net
127.0.0.1  ad.ae.doubleclick.net
127.0.0.1  ad.ar.doubleclick.net
127.0.0.1  ad.au.doubleclick.net
127.0.0.1  ad.be.doubleclick.net
127.0.0.1  ad.br.doubleclick.net #[SunBelt.DoubleClick]
127.0.0.1  ad.ca.doubleclick.net
127.0.0.1  ad.ch.doubleclick.net
127.0.0.1  ad.cl.doubleclick.net
127.0.0.1  ad.cn.doubleclick.net
127.0.0.1  ad.de.doubleclick.net #[Tenebril.Tracking.Cookie]
127.0.0.1  ad.dk.doubleclick.net
127.0.0.1  ad.es.doubleclick.net
127.0.0.1  ad.fi.doubleclick.net
127.0.0.1  ad.fr.doubleclick.net
127.0.0.1  ad.hk.doubleclick.net
127.0.0.1  ad.hu.doubleclick.net
127.0.0.1  ad.ie.doubleclick.net
127.0.0.1  ad.in.doubleclick.net
127.0.0.1  ad.jp.doubleclick.net
127.0.0.1  ad.kr.doubleclick.net
127.0.0.1  ad.it.doubleclick.net
127.0.0.1  ad.nl.doubleclick.net
127.0.0.1  ad.no.doubleclick.net
127.0.0.1  ad.nz.doubleclick.net
127.0.0.1  ad.pl.doubleclick.net
127.0.0.1  ad.pt.doubleclick.net
127.0.0.1  ad.ro.doubleclick.net
127.0.0.1  ad.ru.doubleclick.net
127.0.0.1  ad.se.doubleclick.net
127.0.0.1  ad.sg.doubleclick.net
127.0.0.1  ad.terra.doubleclick.net
127.0.0.1  ad.th.doubleclick.net
127.0.0.1  ad.tw.doubleclick.net
127.0.0.1  ad.uk.doubleclick.net
127.0.0.1  ad.us.doubleclick.net
127.0.0.1  ad.za.doubleclick.net
127.0.0.1  ad.n2434.doubleclick.net
127.0.0.1  creatives.doubleclick.net
127.0.0.1  dfp.doubleclick.net
127.0.0.1  fls.doubleclick.net
127.0.0.1  ir.doubleclick.net
127.0.0.1  iv.doubleclick.net
127.0.0.1  ln.doubleclick.net #[Lycos]
127.0.0.1  m.doubleclick.net
127.0.0.1  m2.doubleclick.net
127.0.0.1  m3.doubleclick.net
127.0.0.1  m.us.doubleclick.net
127.0.0.1  motifcdn.doubleclick.net
127.0.0.1  n3285ad.doubleclick.net
127.0.0.1  n3349ad.doubleclick.net
127.0.0.1  n4403ad.doubleclick.net
127.0.0.1  n479ad.doubleclick.net
127.0.0.1  n609ad.doubleclick.net
127.0.0.1  optout.doubleclick.net
127.0.0.1  optimize.doubleclick.net
127.0.0.1  optimize.3optimization.doubleclick.net
127.0.0.1  paypalssl.doubleclick.net
127.0.0.1  rd.intl.doubleclick.net
127.0.0.1  se1.doubleclick.net
127.0.0.1  twx.doubleclick.net
127.0.0.1  doubleclick.ne.jp
127.0.0.1  www3.doubleclick.net
127.0.0.1  www.doubleclick.net
127.0.0.1  doubleclick.com
127.0.0.1  www2.doubleclick.com
127.0.0.1  www3.doubleclick.com
127.0.0.1  www.doubleclick.com
127.0.0.1  www.messagemedia.com
127.0.0.1  www.performics.com
127.0.0.1  doubleclick.shockwave.com
# [Dynamic Logic]
127.0.0.1  content.dl-rms.com
127.0.0.1  questionmarket.com #[SpySweeper.Spy.Cookie]
127.0.0.1  amch.questionmarket.com #[McAfee.Cookie-Questionmarket]
127.0.0.1  ch.questionmarket.com #[Panda.Spyware:Cookie]
127.0.0.1  survey.questionmarket.com
127.0.0.1  www.questionmarket.com #[Ad-Aware.Tracking.Cookie]
# [Dynamic Network Services]
127.0.0.1  cxoadfarm.dyndns.info #[Ad-Aware.Tracking.Cookie]
127.0.0.1  cxoreport.dnsalias.net
# [ebusiness-sap]
127.0.0.1  armbender.com #[UCSearch.ucUCSearch][W32.Adclicker.F.Trojan]
127.0.0.1  www.armbender.com #[HJTH.UCSearch/ArmBender]
127.0.0.1  flowers.theshoppingwiz.com
127.0.0.1  www.theshoppingwiz.com
127.0.0.1  www.toonah.com
127.0.0.1  www.zuvio.biz
127.0.0.1  zuvio.com #[UCSearch.ucUCSearch]
127.0.0.1  www.zuvio.com #[Adware.OpenSite][ADW_OPENSITE.M]
127.0.0.1  www.zuvio.net
# [Effective-i][Ronen Shilo][Platforma Online Ltd]
127.0.0.1  search.effectivebrand.com
127.0.0.1  users.effectivebrand.com #[SunBelt.IEMenuExtension Toolbar]
127.0.0.1  www.effectivebrand.com #[ADW_IMENEXT.A][Adware.IEMenuExt]
127.0.0.1  www.thesearchaccelerator.com #[Ewido.Spyware.EffectiveBrandToolbar]
127.0.0.1  www.similarplus.com
127.0.0.1  download.ucmore.com #[Adware.UCMore]
127.0.0.1  users.ucmore.com #[Adware-UCMore.dr][F-Secure.UCmore]
127.0.0.1  sponsor2.ucmore.com #[IEMenuExtension Toolbar]
127.0.0.1  www.ucmore.com #[ADW_IMENEXT.A][Win32/Adware.UCmore]
127.0.0.1  www.ucmore.net
127.0.0.1  www.ucmoreinfo.com
# [EnBrowser]
127.0.0.1  www.enbrowser.com #[Adware.WinBo]
127.0.0.1  www.nbrowser.com #[Trojan.Agent.winbo32]
# [Engage Marketing]
127.0.0.1  www.adwarefinder.com #[AdWare.Win32.SideSearch.g]
127.0.0.1  contextualtoolbar.com #[Win32/Adware.SideSearch]
127.0.0.1  www.contextualtoolbar.com #[Adware.ContextualToolbar]
127.0.0.1  www.engagemarketing.com #[Whois.Blacklisted]
127.0.0.1  www.kingtutgame.com #[AdWare.Win32.SideSearch.g]
# [ESD Technologies][Mark Jackson][Digital Delivery LLC]
127.0.0.1  1-dvd-player.com #[AdWare.GoWebSite]
127.0.0.1  www.1stairfare.info #[ADW_INETSPEAK.A]
127.0.0.1  1st-software-downloads.com
127.0.0.1  www.1st-software-downloads.com
127.0.0.1  1stsoftwaredownloads.com #[Adware/NewtonKnows]
127.0.0.1  www.1stsoftwaredownloads.com
127.0.0.1  adblaster2.info
127.0.0.1  www.adblaster2.info
127.0.0.1  bigsearch.biz
127.0.0.1  www.bigsearch.biz
127.0.0.1  www.crazaa.com
127.0.0.1  digital-delivery.us #[SecurityRisk.MatrixSS]
127.0.0.1  www.dvd-download-free.com
127.0.0.1  www.dvd-music-downloads.com
127.0.0.1  www.esdng5.com
127.0.0.1  www.esdpc.com
127.0.0.1  free-movies-download.com #[AdWare.GoWebSite]
127.0.0.1  www.free-movies-download.com #[SunBelt.Free-Movies-Download.com]
127.0.0.1  imesh-download-imesh.com
127.0.0.1  www.matrix-screensaver.com
127.0.0.1  matrix-screensaver.net #[SiteAdvisor.matrix-screensaver.net]
127.0.0.1  www.matrix-screensaver.net
127.0.0.1  morpheus-download-morpheus.com #[Trojan-Clicker.Win32.VB.gn]
127.0.0.1  www.morpheus-downloads-morpheus-download.com
127.0.0.1  www.movies-download-movies.com
127.0.0.1  mp3-file-downloads.com
127.0.0.1  www.mp3-file-downloads.com
127.0.0.1  www.music-download-music.com 
127.0.0.1  netwebsearch.com
127.0.0.1  www.netwebsearch.com #[adblaster2.info][SysIdle]
127.0.0.1  netwebsearch2.com #[Adware.AdBlaster]
127.0.0.1  www.netwebsearch2.com
127.0.0.1  netsearch.info
127.0.0.1  www.netsearch.info
127.0.0.1  www.polymer-solvents.com
127.0.0.1  quality-shopping.info
127.0.0.1  www.quality-shopping.info
127.0.0.1  www.searchmaster.org
127.0.0.1  www.websearcher.info #[netwebsearch.com]
127.0.0.1  windows-xp-download-upgrades.com
127.0.0.1  winmx-download-winmx.com #[Trojan-Clicker.Win32.VB.gn]
127.0.0.1  www.winmx-download-winmx.com
127.0.0.1  zoneprotect.com #[Trojan-Clicker.Win32.VB.gn]
127.0.0.1  www.zoneprotect.com #[Rogue/Suspect]
# [EST Domains][Intercage]
127.0.0.1  xhpro.com
127.0.0.1  bastion.xhpro.com #[MHTMLRedir.Exploit]
127.0.0.1  meduza.xhpro.com
# [ESTDOMAINS - Various]
127.0.0.1  www.a311.com #[Kephyr.PUP]
127.0.0.1  abc-porno.net
127.0.0.1  about-porno.com
127.0.0.1  accessporno.net
127.0.0.1  adprotect.com #[eTrust.SpyShield.Ad-Protect]
127.0.0.1  www.adprotect.com
127.0.0.1  adultsexpro.com #[Trojan.Codec]
127.0.0.1  amazingsexmovie.com #[Win32/Genetik]
127.0.0.1  www.amazingsexmovie.com
127.0.0.1  angelsfucked.com #[TROJ_SMALL.SB]
127.0.0.1  www.angelsfucked.com
127.0.0.1  antispysolutions.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.antispysolutions.com
127.0.0.1  antivermins.com #[Win32/Adware.AntiVermins]
127.0.0.1  www.antivermins.com #[McAfee.Adware-AntiVerm]
127.0.0.1  antivirusgolden.com #[McAfee.AVGold]
127.0.0.1  www.antivirusgolden.com #[Adware-Spyware/GoldenVirus.A][Rogue/Suspect]
127.0.0.1  babe-girls.com #[Malicious.Links]
127.0.0.1  www.babe-girls.com
127.0.0.1  basicsex.net
127.0.0.1  bondageclips.net #[Videoscash][server down?]
127.0.0.1  www.bondageclips.net
127.0.0.1  center-porno.com
127.0.0.1  chat-porn.net
127.0.0.1  compporno.com
127.0.0.1  comp-porno.com
127.0.0.1  www.connectingslice.com #[JS/TrojanDownloader.Psyme.CZ.Gen]
127.0.0.1  contact-porn.net
127.0.0.1  contact-sex.com
127.0.0.1  controlporno.com
127.0.0.1  devils-porn.net
127.0.0.1  divineteens.com #[IFrame.Exploit]
127.0.0.1  www.divineteens.com
127.0.0.1  domainserror.com
127.0.0.1  www.domainserror.com #[Trojan.Win32.DNSChanger.gx]
127.0.0.1  driveporn.net
127.0.0.1  engine-porno.net
127.0.0.1  export-sex.net
127.0.0.1  extra-porno.net
127.0.0.1  feedpublic.com #[Spamdexing]
127.0.0.1  feevideo.net #[Spamdexing]
127.0.0.1  search.feevideo.net
127.0.0.1  findallgood.com
127.0.0.1  flowers.findallgood.com #[Spamdexing]
127.0.0.1  www.findallgood.com
127.0.0.1  freeimageheaven.com #[Trojan.Codec]
127.0.0.1  www.freeimageheaven.com
127.0.0.1  www.freshvids.net #[server down?]
127.0.0.1  helpporno.net
127.0.0.1  hostporno.net
127.0.0.1  host-porno.com
127.0.0.1  iqcounter.com
127.0.0.1  09.justcountrr.org
127.0.0.1  _218_.justcountrr.org
127.0.0.1  key-sex.com
127.0.0.1  www.killandclean.com #[Rogue/Suspect][Win32/Adware.KAC]
127.0.0.1  limon-finder.com #[MHTMLRedir.Exploit]
127.0.0.1  www.limon-finder.com
127.0.0.1  line-porno.net
127.0.0.1  micro-porno.net
127.0.0.1  microporno.net
127.0.0.1  www.mp3sugar.com
127.0.0.1  mypornoxxx.com
127.0.0.1  www.mypornoxxx.com #[Javascript.Exploit]
127.0.0.1  name-porno.com
127.0.0.1  name-porno.net
127.0.0.1  name-sex.net
127.0.0.1  networkporn.net
127.0.0.1  nnew-adult.info #[Win32/TrojanDownloader.Nurech.NAT]
127.0.0.1  notetol.com #[SunBelt.Trojan.LinkOptimizer]
127.0.0.1  www.notetol.com #[AdWare.Win32.LinkOptimizer.a]
127.0.0.1  secure.onemomentpay.com #[perfectcleaner2007.com]
127.0.0.1  part-porno.com
127.0.0.1  passtosites.net #[Win32/TrojanDownloader.Zlob]
127.0.0.1  www.passtosites.net
127.0.0.1  pilot-sex.net
127.0.0.1  playporno.net
127.0.0.1  pleasure-porno.com
127.0.0.1  popularporn.net
127.0.0.1  protectwin.com #[Hoax.Win32.Renos.hm][server down?]
127.0.0.1  www.protectwin.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  related-porno.com
127.0.0.1  related-sex.com
127.0.0.1  review-porno.net
127.0.0.1  roomporno.net
127.0.0.1  scan-porno.net
127.0.0.1  www.search-toolbar.com #[Trojan.Magise]
127.0.0.1  selectedsecurity.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.selectedsecurity.com
127.0.0.1  spymarshal.com #[Win32/Adware.SpySheriff]
127.0.0.1  www.spymarshal.com #[TR/Renos.28160]
127.0.0.1  www.teslaplus.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  uspocketpc.com #[Javascript.Exploit]
127.0.0.1  vaxvideo.net
127.0.0.1  www.vaxvideo.net
127.0.0.1  virusblast.com #[Win32/Adware.VirusBlast]
127.0.0.1  www.virusblast.com #[Symantec.VirusBlast]
127.0.0.1  virusrescue.com #[Win32/Adware.VirusRescue]
127.0.0.1  www.virusrescue.com #[Symantec.VirusRescue]
127.0.0.1  washerner.com #[Win32/TrojanDownloader.Agent.BQ]
127.0.0.1  pool.westpop.com #[Kephyr.PUP]
127.0.0.1  www.wofldsex.com #[MHTMLRedir.Exploit]
127.0.0.1  x-traffic.biz
127.0.0.1  www.x-traffic.biz
127.0.0.1  xxxvidsblog.com #[Trojan.Codec]
127.0.0.1  zcodec.com #[Win32/TrojanDownloader.Zlob]
127.0.0.1  www.zcodec.com
127.0.0.1  zuluzazaee.com #[Spamdexing]
# [ESTDOMAINS via AASYS.BIZ Group]
127.0.0.1  www.amxgames.net #[Troj/Dloader-GR]
127.0.0.1  auto.daily-weather.com #[Troj/Dloader-IP]
127.0.0.1  www2.daily-weather.com #[TrojanDownloader.INService]
127.0.0.1  china.dalexcars.com
127.0.0.1  www.dalexcars.com #[Troj/Istbar-AK]
127.0.0.1  chive.darpmusic.com #[PcTools.DarpMusic]
127.0.0.1  ddl-help.info #[Win32/TrojanDownloader.INService]
127.0.0.1  xmirror.us #[Trojan.Downloader.INService.Gen]
127.0.0.1  lists.xmirror.us #[Troj/Dloader-IN]
127.0.0.1  www.xmirror.us
# [ESTDOMAINS via Abraham Biderman][Erik Asarian]
127.0.0.1  adultbookings.com #[Malicious.Links]
127.0.0.1  adultan.com
127.0.0.1  www.adultan.com
127.0.0.1  adultau.com
127.0.0.1  www.adultau.com
127.0.0.1  adultfilmsite.com
127.0.0.1  www.adultfilmsite.com
127.0.0.1  adultmovieplus.com
127.0.0.1  www.adultmovieplus.com #[Videoscash]
127.0.0.1  adultsper.com
127.0.0.1  www.adultsper.com
127.0.0.1  adulttow.com
127.0.0.1  www.adulttow.com
127.0.0.1  clubxxxvideo.com
127.0.0.1  www.clubxxxvideo.com
127.0.0.1  cutadult.com
127.0.0.1  www.cutadult.com
127.0.0.1  galleryclick.net
127.0.0.1  www.galleryclick.net
127.0.0.1  gallerypictures.net
127.0.0.1  www.gallerypictures.net
127.0.0.1  greatadultvideo.com
127.0.0.1  www.greatadultvideo.com
127.0.0.1  hardcorevideosite.com
127.0.0.1  www.hardcorevideosite.com
127.0.0.1  loweradult.com
127.0.0.1  www.loweradult.com
127.0.0.1  mega-adult.com
127.0.0.1  www.mega-adult.com
127.0.0.1  sureadult.com
127.0.0.1  www.sureadult.com
127.0.0.1  xxxallvideo.com
127.0.0.1  www.xxxallvideo.com
127.0.0.1  xxxmovietour.com
127.0.0.1  www.xxxmovietour.com
127.0.0.1  xxxteenfilm.com
127.0.0.1  www.xxxteenfilm.com
127.0.0.1  xxxzonevideo.com
127.0.0.1  www.xxxzonevideo.com
# [ESTDOMAINS via Abraham Niakate][Carl Feafter]
127.0.0.1  club-adult.net
127.0.0.1  euroadultsex.com
127.0.0.1  fun-adult.com
127.0.0.1  galleryalbum.net #[Trojan.Codec]
127.0.0.1  galleryhere.net
127.0.0.1  galleryteen.net
127.0.0.1  goadult.net
127.0.0.1  moviexxxhotel.com
127.0.0.1  sexadultguide.com
127.0.0.1  sexadultstar.com
127.0.0.1  usaadultvideo.com
127.0.0.1  visitadult.com
127.0.0.1  worldadultvideo.com
# [ESTDOMAINS via Adult Comix Group]
127.0.0.1  adultcomix.biz
127.0.0.1  free.adultcomix.biz
127.0.0.1  alivegirls.com #[Malicious.Links.Codec]
127.0.0.1  www.alivegirls.com #[SiteAdvisor.alivegirls.com]
127.0.0.1  artcomix.com
127.0.0.1  top.artcomix.com
127.0.0.1  www.artcomix.com
127.0.0.1  cartoonpornguide.com
127.0.0.1  free.cartoonpornguide.com
127.0.0.1  www.cartoonpornguide.com
127.0.0.1  dvdhentai.net
127.0.0.1  gallfree.com #[Trojan.Codec]
127.0.0.1  img.gallfree.com
127.0.0.1  www.gallfree.com
127.0.0.1  toon-families.com
127.0.0.1  www.toon-families.com
127.0.0.1  toonfamilies.net
127.0.0.1  www.toonfamilies.net
127.0.0.1  wildmistress.com
127.0.0.1  www.wildmistress.com
# [ESTDOMAINS via Alexei Ardashev]
127.0.0.1  coolsearch.biz #[SiteAdvisor.coolsearch.biz]
127.0.0.1  www.coolsearch.biz
127.0.0.1  gigasearch.biz #[AdWare.Giga]
127.0.0.1  www.gigasearch.biz
127.0.0.1  search-paga.com
127.0.0.1  www.search-paga.com #[SiteAdvisor.search-paga.com]
# [ESTDOMAINS via Amadou Niane]
127.0.0.1  access-porn.net
127.0.0.1  browse-porn.com #[Trojan.Codec]
127.0.0.1  business-porn.net
127.0.0.1  comp-porn.net
127.0.0.1  control-porn.net
127.0.0.1  controlporn.com
127.0.0.1  engineporn.net
127.0.0.1  funporn.net
127.0.0.1  line-porn.com
127.0.0.1  line-porn.net
127.0.0.1  party-porn.net
127.0.0.1  try-porn.com
127.0.0.1  reviewporn.net
127.0.0.1  scanporn.net
127.0.0.1  scan-porn.com
127.0.0.1  service-porn.net
# ESTDOMAINS via Andersen Claus]
127.0.0.1  allprotections.com
127.0.0.1  www.allprotections.com
# [ESTDOMAINS via Andre Solar Group]
127.0.0.1  advancedhunt.com #[Google Warning]
127.0.0.1  www.advancedhunt.com #[JS/Exploit.IEPageSpoof]
127.0.0.1  goporn.us
127.0.0.1  www.goporn.us
127.0.0.1  www.impliedscripting.com
127.0.0.1  j.javaforge.info
127.0.0.1  www.javaforge.info
127.0.0.1  solar-porn.com
127.0.0.1  topdatasearch.com
127.0.0.1  www.topdatasearch.com
127.0.0.1  xxxseek.org
127.0.0.1  www.xxxseek.org #[JS/Exploit.IEPageSpoof]
# [ESTDOMAINS via Andrew Fredbeck][Andrew Frey]
127.0.0.1  abcporno.net
127.0.0.1  access-porno.com
127.0.0.1  basic-porno.net
127.0.0.1  center-porn.com
127.0.0.1  city-porn.net
127.0.0.1  driveporno.com
127.0.0.1  ex-porn.net #[Trojan.Codec]
127.0.0.1  extasy-porno.com
127.0.0.1  fun-porno.com
127.0.0.1  global-porn.net
127.0.0.1  helpporno.com
127.0.0.1  inc-porn.com
127.0.0.1  play-porno.com
127.0.0.1  plusporno.net
127.0.0.1  pornocontrol.net
127.0.0.1  porno-go.com
127.0.0.1  porno-help.com
127.0.0.1  porno-scan.net
127.0.0.1  porno-seek.net
127.0.0.1  porno-visit.com
127.0.0.1  related-porn.net
127.0.0.1  seaporno.com
127.0.0.1  visitporn.net
127.0.0.1  vivaporno.net
127.0.0.1  want-porno.net
# [ESTDOMAINS via Andrew Michael]
127.0.0.1  accessadult.net
127.0.0.1  engineadult.com
127.0.0.1  helpadult.net
127.0.0.1  partyadult.net #[Trojan.Codec]
127.0.0.1  scanadult.net
# [ESTDOMAINS via Andy Placid][Andrew Krukov]
127.0.0.1  www.cellgateinc.com
127.0.0.1  ****-a-land.com
127.0.0.1  www.****-a-land.com
127.0.0.1  www.hqualityporn.com
127.0.0.1  www.treffend.com
# [ESTDOMAINS via Angela Sage]
127.0.0.1  extasyporn.net
127.0.0.1  extasy-porn.com #[Trojan.Codec]
127.0.0.1  extra-porn.net
127.0.0.1  fake-porn.com
127.0.0.1  heroporn.net
127.0.0.1  www.heroporn.net
127.0.0.1  hit-porn.net
127.0.0.1  join-porn.net
127.0.0.1  pornbrowse.net
127.0.0.1  porn-business.net
127.0.0.1  porn-comp.net
127.0.0.1  porncontrol.net
127.0.0.1  pornlook.net
127.0.0.1  pornvisit.net
127.0.0.1  shtorm-porn.com
127.0.0.1  shtormporn.net
127.0.0.1  standard-porn.net
127.0.0.1  viva-porn.net
127.0.0.1  zero-porn.com
# [ESTDOMAINS via Angelo Sabatelli]
127.0.0.1  group-adult.com #[Trojan.Codec]
127.0.0.1  landadult.com
127.0.0.1  plusadult.net
127.0.0.1  time-adult.com
127.0.0.1  tryadult.net
127.0.0.1  use-adult.com
127.0.0.1  visit-adult.com
127.0.0.1  want-adult.net
# [ESTDOMAINS via Anne Kintzer]
127.0.0.1  porn-about.net
127.0.0.1  porn-club.net
127.0.0.1  porncontact.net
127.0.0.1  porn-drive.com
127.0.0.1  porn-ex.com #[Trojan.Codec]
127.0.0.1  porn-extasy.com
127.0.0.1  porn-extra.net
127.0.0.1  porn-fake.com
127.0.0.1  porn-hero.net
127.0.0.1  porn-hit.net
127.0.0.1  pornjust.com
127.0.0.1  porn-love.net
127.0.0.1  pornnaked.net
127.0.0.1  porn-network.net
127.0.0.1  porn-pop.net
127.0.0.1  porn-standard.com
127.0.0.1  porn-want.net
127.0.0.1  pornviva.com
127.0.0.1  porn-zero.net
127.0.0.1  porshtorm.com
# ESTDOMAINS via Anta Niang]
127.0.0.1  basicadult.com
127.0.0.1  centeradult.com
127.0.0.1  contact-adult.com
127.0.0.1  custom-adult.com #[Trojan.Codec]
127.0.0.1  micro-adult.com
127.0.0.1  popularadult.net
127.0.0.1  relatedadult.net
# [ESTDOMAINS via Antex]
127.0.0.1  www.awm-cash.com #[Coulomb Dialer]
127.0.0.1  friendslinks.com
127.0.0.1  www.friendslinks.com
127.0.0.1  ****-access.com #[SiteAdvisor.****-access.com]
127.0.0.1  www.****-access.com
127.0.0.1  www.grodno-online.com
127.0.0.1  serialsbox.com
127.0.0.1  www.serialsbox.com #[JS/TrojanDownloader.Agent.Z][server down?]
127.0.0.1  totsex.net #[Parked.redirect]
127.0.0.1  www.x-park.net #[server down?]
127.0.0.1  yournetaccess.com #[SiteAdvisor.yournetaccess.com]
127.0.0.1  www.yournetaccess.com #[Videoscash]
# [ESTDOMAINS via AntiSpyware Coalition]
127.0.0.1  exedollars.com
127.0.0.1  www.exedollars.com
# [ESTDOMAINS via Arijan Fera]
127.0.0.1  adultvidsportal.com
127.0.0.1  www.adultvidsportal.com
127.0.0.1  dailybigvideos.com
127.0.0.1  www.dailybigvideos.com
127.0.0.1  exclusivexxxclips.com
127.0.0.1  www.exclusivexxxclips.com
127.0.0.1  freenichemovies.com
127.0.0.1  www.freenichemovies.com
127.0.0.1  givemepornvids.com
127.0.0.1  www.givemepornvids.com
127.0.0.1  pornmoviesindex.com
127.0.0.1  www.pornmoviesindex.com #[Trojan.Codec]
127.0.0.1  todaysbestclip.com
127.0.0.1  www.todaysbestclip.com
# [ESTDOMAINS via ASecure][Psak Nikolina]
127.0.0.1  alldnserrors.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.alldnserrors.com
127.0.0.1  allsecuritysite.com
127.0.0.1  www.allsecuritysite.com
127.0.0.1  topsecuritypage.com
127.0.0.1  www.topsecuritypage.com
# [ESTDOMAINS via Ase Traving]
127.0.0.1  asecurityissue.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.asecurityissue.com
# [ESTDOMAINS via bill pip]
127.0.0.1  www.amazon-girl.com
127.0.0.1  www.babespet.com
127.0.0.1  babesfoto.com #[Malicious.Links]
127.0.0.1  www.farm6.com
127.0.0.1  www.farmers6.com
127.0.0.1  www.jungle6.com
127.0.0.1  maidenpix.com
127.0.0.1  nastyyoungass.com
127.0.0.1  pinkbadgirls.com
127.0.0.1  www.pinkbadgirls.com #[Google.Warning]
127.0.0.1  www.pixyoung.com #[Javascript.Exploit]
127.0.0.1  www.summer-beast.com
# [ESTDOMAINS via Bootastic Computers]
127.0.0.1  find-biz.info #[kklik2]
127.0.0.1  www.find-biz.info
127.0.0.1  www.24-7find.com
127.0.0.1  www.buy-find.info 
127.0.0.1  www.cyber-find.info
127.0.0.1  searche.info
# [ESTDOMAINS via Christian Leo]
127.0.0.1  dailyxratedimages.com
127.0.0.1  www.dailyxratedimages.com #[Google.Warning]
127.0.0.1  ximagecollection.com #[VideosCash]
127.0.0.1  www.ximagecollection.com
# [ESTDOMAINS via Christian Phil Moen]
127.0.0.1  asafetypage.com
127.0.0.1  www.asafetypage.com
127.0.0.1  protectionssoft.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.protectionssoft.com
# [ESTDOMAINS via Daniel Astuto]
127.0.0.1  adultloan.net #[Google.Warning]
127.0.0.1  adultsea.net #[Trojan.Codec]
127.0.0.1  comp-porn.com
127.0.0.1  engineporn.com
127.0.0.1  lineporn.net
127.0.0.1  pleasure-porn.net #[Trojan.Codec]
127.0.0.1  seek-porn.net
127.0.0.1  shopporn.net
# [ESTDOMAINS via home DJWashington]
127.0.0.1  dirtymoviesempire.com
127.0.0.1  www.dirtymoviesempire.com
127.0.0.1  starsoftheporn.com #[Trojan.Codec]
# [ESTDOMAINS via Donald Straub]
127.0.0.1  1200land.com #[MHTMLRedir.Exploit][VBS/Exploit.Phel.A]
127.0.0.1  www.1200land.com
# [ESTDOMAINS via Endi Streff]
127.0.0.1  crackdb.com #[Trojan.Clicker.Small.IS]
127.0.0.1  www.crackdb.com
127.0.0.1  cracksplanet.com #[Trojan.Clicker.Small.IS]
127.0.0.1  www.cracksplanet.com
127.0.0.1  crackzplanet.com #[StopBadware.Warning]
127.0.0.1  www.crackzplanet.com
127.0.0.1  warewz.ws
# [ESTDOMAINS via Erik Niklas]
127.0.0.1  alwaysfreshpornvideos.com
127.0.0.1  www.alwaysfreshpornvideos.com
127.0.0.1  clipsforadults.com
127.0.0.1  www.clipsforadults.com #[Trojan.Codec]
127.0.0.1  freedailyxvids.com
127.0.0.1  www.freedailyxvids.com
127.0.0.1  mpegsgallery.com
127.0.0.1  www.mpegsgallery.com
# [ESTDOMAINS via EstBill Limited]
127.0.0.1  adware-bazooka.com #[Win32/Adware.ADWareBazooka]
127.0.0.1  www.adware-bazooka.com
127.0.0.1  adware-punisher.com #[AntiVir.ADSPY/Punisher.A.1]
127.0.0.1  www.adware-punisher.com
127.0.0.1  hit-virus.com #[Win32/Adware.HitVirus]
127.0.0.1  www.hit-virus.com
127.0.0.1  spy-iblock.com
127.0.0.1  www.spy-iblock.com
127.0.0.1  the-spy-guard.com #[Win32/Adware.HitVirus]
127.0.0.1  www.the-spy-guard.com
# [ESTDOMAINS via ESTHOST][Peter Isson][Marko Martinen]
127.0.0.1  www.antincsoft.com
127.0.0.1  www.betting-cards-games.com
127.0.0.1  www.cardsgames.net
127.0.0.1  delpyware.com
127.0.0.1  easyantispy.com
127.0.0.1  www.easysurfe.com
127.0.0.1  freespyscanner.com #[Webhelper.CWS List]
127.0.0.1  www.freespyscanner.net #[clearsurfing.net]
127.0.0.1  www.funnygirls.com
127.0.0.1  getspecialdeals.com #[24-7find.com]
127.0.0.1  girl4sex.org
127.0.0.1  girls4rent.net
127.0.0.1  www.girlsforsex.net
127.0.0.1  homesearcheuro.com
127.0.0.1  jackandpoker.net #[ADW_MSNLIST.B]
127.0.0.1  livegabmling.com #[ADW_MSNLIST.B]
127.0.0.1  www.meet-wet-holes.com
127.0.0.1  meet-your-love.net
127.0.0.1  www.msnlist.com #[Adware.FindSpyware][ADW_CLICKER.D]
127.0.0.1  pcfileprotect.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  pickup-ur-girl.net
127.0.0.1  pickup-ur-girl.com
127.0.0.1  pokerandmoney.net #[ADW_MSNLIST.B]
127.0.0.1  ppcprotect.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  protectsoft.net
127.0.0.1  www.protectsoft.net
127.0.0.1  realitycasino.net
127.0.0.1  rooms4poker.com
127.0.0.1  sexygirlfriends.org
127.0.0.1  pool.sexpopbar.com #[westpop.com]
127.0.0.1  softantispy.com
127.0.0.1  www.softantispy.com
127.0.0.1  spybotremover.net
127.0.0.1  www.spybotremover.net
127.0.0.1  www.spyprotect.org
127.0.0.1  www.spywarecleaner.org #[findspyware.net]
127.0.0.1  spywaremustdie.com #[clearsurfing.net]
127.0.0.1  www.spywaremustdie.com
127.0.0.1  spywarewasher.net
127.0.0.1  www.spywarewasher.net
127.0.0.1  takethischiks.com
127.0.0.1  www.thequicklink.com
127.0.0.1  www.topxxxdvd.net
127.0.0.1  usefulholes.com
127.0.0.1  usefulholes.net
127.0.0.1  www.usefullsoft.com
127.0.0.1  usefullsoft.net
127.0.0.1  windowprotectorkit.com
127.0.0.1  windowspyware.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.yourblackjack.com
# [ESTDOMAINS via est-host][Vladimir Tsas]
127.0.0.1  all-mature-babes.com #[Videoscash]
127.0.0.1  bestadultgals.com #[Videoscash]
127.0.0.1  www.bestadultgals.com
127.0.0.1  megatds.com #[Panda.Adware/Megatds]
127.0.0.1  admintds.megatds.com
127.0.0.1  tds.megatds.com
127.0.0.1  www.megatds.com
127.0.0.1  pornothumbgals.com
# [ESTDOMAINS via Fatim Kusher]
127.0.0.1  www.adult-trade.net
127.0.0.1  22pics.com #[Videoscash]
127.0.0.1  www.22pics.com
127.0.0.1  www.alexa69.com
127.0.0.1  amazon4sex.com
127.0.0.1  www.amazon4sex.com #[MHTMLRedir.Exploit]
127.0.0.1  free-video-post.com #[Videoscash]
127.0.0.1  www.free-video-post.com
127.0.0.1  www.iframestat.com
127.0.0.1  pornbook.net #[Videoscash]
127.0.0.1  www.pornbook.net
127.0.0.1  pornhit.net #[Videoscash]
127.0.0.1  www.pornhit.net
127.0.0.1  pornwoods.com
127.0.0.1  www.pornwoods.com
127.0.0.1  video-post.org
127.0.0.1  www.video-post.org
127.0.0.1  www.worldsex.co.yu
# [ESTDOMAINS via Fedor Kiriakini]
127.0.0.1  dateporn.net
127.0.0.1  digital-porn.net #[Trojan.Codec]
127.0.0.1  host-porn.net
127.0.0.1  micro-porn.net
127.0.0.1  nameporn.net
127.0.0.1  portal-porn.com
127.0.0.1  powerporn.net
127.0.0.1  site-porn.net
# [ESTDOMAINS via FetBiz Co]
127.0.0.1  www.bestsearchsite.net
127.0.0.1  lookforthe.net
127.0.0.1  teenpics.lookforthe.net #[Videoscash]
127.0.0.1  www.lookforthe.net
127.0.0.1  www.searchgo.us
# [ESTDOMAINS via Geo Group][Orange Bob]
127.0.0.1  callmachine.net #[SiteAdvisor.callmachine.net]
127.0.0.1  www.callmachine.net
127.0.0.1  extraprivacy.com
127.0.0.1  www.extraprivacy.com
127.0.0.1  system-stable.com
127.0.0.1  www.system-stable.com
# [ESTDOMAINS via George Nikas]
127.0.0.1  cruiseporn.com
127.0.0.1  porndrive.net #[Trojan.Codec]
127.0.0.1  pornhelp.net
127.0.0.1  porn-global.net
127.0.0.1  porn-go.net
127.0.0.1  porn-party.net
127.0.0.1  porn-play.net
# [ESTDOMAINS via Gerard Gast]
127.0.0.1  iesafetywarning.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.iesafetywarning.com
127.0.0.1  uptodateprotect.com
127.0.0.1  www.uptodateprotect.com
# [ESTDOMAINS via Giname Media][Boris Klimov][PR InterMedia]
127.0.0.1  www.annathumbs.com #[privacyHTA.dll]
127.0.0.1  apornmovie.com
127.0.0.1  www.apornmovie.com
127.0.0.1  www.cindythumbs.com #[SiteAdvisor.cindythumbs.com]
127.0.0.1  www.emilythumbs.com
127.0.0.1  www.emmathumbs.com
127.0.0.1  www.ginamemedia.com
127.0.0.1  www.hardcore-sex-movies.com #[Trojan.StartPage.L][StartPage-HJ]
127.0.0.1  www.jacobporn.com
127.0.0.1  jessicathumbs.com
127.0.0.1  www.jessicathumbs.com #[Malicious Links]
127.0.0.1  www.joshuaporn.com
127.0.0.1  www.madisonthumbs.com
127.0.0.1  www.oliviathumbs.com
127.0.0.1  rudesexlinks.com
127.0.0.1  www.rudesexlinks.com
# [ESTDOMAINS via Gittel Hartman]
127.0.0.1  extasyporno.net
127.0.0.1  joinporno.net #[Trojan.Codec]
127.0.0.1  loanporno.com
127.0.0.1  standard-porno.com
# [ESTDOMAINS via Haber Gisela]
127.0.0.1  aboutadultsex.com
127.0.0.1  www.aboutadultsex.com
127.0.0.1  adultby.com
127.0.0.1  www.adultby.com
127.0.0.1  adultcollect.com
127.0.0.1  www.adultcollect.com
127.0.0.1  adultdvdsfor.com
127.0.0.1  www.adultdvdsfor.com
127.0.0.1  adultgamesfor.com
127.0.0.1  www.adultgamesfor.com
127.0.0.1  adultsexcar.com #[Videoscash]
127.0.0.1  www.adultsexcar.com
127.0.0.1  adultstarworld.com
127.0.0.1  adultvideodot.com
127.0.0.1  www.adultvideodot.com
127.0.0.1  adultzoneworld.com
127.0.0.1  www.adultzoneworld.com
127.0.0.1  adult-help.net
127.0.0.1  adult-name.net #[Trojan.Codec]
127.0.0.1  adult-popular.com
127.0.0.1  adult-room.net
127.0.0.1  adultexport.net
127.0.0.1  adultfast.net
127.0.0.1  adultpilot.net
127.0.0.1  findadultsex.com #[Videoscash]
127.0.0.1  www.findadultsex.com
127.0.0.1  freeeadultvideo.com
127.0.0.1  www.freeeadultvideo.com
127.0.0.1  hotxxxadult.com
127.0.0.1  www.hotxxxadult.com
127.0.0.1  theadulteye.com
127.0.0.1  www.theadulteye.com
127.0.0.1  theadultpost.com
127.0.0.1  www.theadultpost.com
127.0.0.1  worldbestadult.com
127.0.0.1  www.worldbestadult.com
127.0.0.1  xxxadultgold.com
127.0.0.1  www.xxxadultgold.com
# [ESTDOMAINS via Henrih Hamilton]
127.0.0.1  ls0.net
127.0.0.1  4-v.net
# [Henry Bison]
127.0.0.1  free-spy-cam.net #[McAfee.QlowZones-25]
127.0.0.1  getthis4free.com
127.0.0.1  www.getthis4free.com
127.0.0.1  terra.hbison.com
127.0.0.1  hcworld.com
127.0.0.1  free.hcworld.com
127.0.0.1  terra.hcworld.com #[McAfee.QlowZones-25]
127.0.0.1  web-cams-chat.com
127.0.0.1  your-searcher.com #[CWS.IEengine][StartPage-DQ]
# [ESTDOMAINS via home Mitch Chudinov]
127.0.0.1  aka-root.com
127.0.0.1  dancefox.net
127.0.0.1  nafleite.com
127.0.0.1  up-host.com
127.0.0.1  www.x-kernel.com
# [ESTDOMAINS via Hunkins & Garret Inc][Timothy Garret]
127.0.0.1  urgentsystemupdate.biz #[Rogue/Suspect.Affiliate.sites]
127.0.0.1  www.urgentsystemupdate.biz #[McAfee.FakeAlert-B]
127.0.0.1  urgentsystemupdate.com
127.0.0.1  www.urgentsystemupdate.com
# [ESTDOMAINS via Ivan]
127.0.0.1  coolnetsearch.com #[SiteAdvisor.coolnetsearch.com]
127.0.0.1  juicymatures.com #[MHTMLRedir.Exploit]
127.0.0.1  www.juicymatures.com
127.0.0.1  page-x.com
127.0.0.1  transparty.net #[searchanyway.com]
127.0.0.1  www.transparty.net
127.0.0.1  xxx-mom.com #[IFrame.Exploit][Videoscash]
127.0.0.1  www.xxx-mom.com
# [ESTDOMAINS via Ivan Kovpak][Oli Othamar]
127.0.0.1  bestdailymovies.com #[Videoscash]
127.0.0.1  www.bestdailymovies.com
127.0.0.1  todaysfreeclips.com
127.0.0.1  www.todaysfreeclips.com
# [ESTDOMAINS via Ivan Marousseev]
127.0.0.1  allaboutgirl.com
127.0.0.1  www.allaboutgirl.com
127.0.0.1  analmaids.net
127.0.0.1  www.analmaids.net #[Malicious.Links.DriveCleaner]
127.0.0.1  angel-archives.org
127.0.0.1  www.angel-archives.org
127.0.0.1  girlwelove.com
127.0.0.1  www.girlwelove.com #[Malicious.Links.Codec]
127.0.0.1  glamour-videos.net
127.0.0.1  www.glamour-videos.net
127.0.0.1  herfirstdv.org
127.0.0.1  www.herfirstdv.org
127.0.0.1  moneybackporn.com
127.0.0.1  www.moneybackporn.com
127.0.0.1  pleasure-archives.org
127.0.0.1  www.pleasure-archives.org
127.0.0.1  powerlover.com
127.0.0.1  www.powerlover.com
127.0.0.1  realfuckingcouples.org
127.0.0.1  www.realfuckingcouples.org
127.0.0.1  shegotswitched.org
127.0.0.1  www.shegotswitched.org
127.0.0.1  tgp-service.com
127.0.0.1  www.tgp-service.com
127.0.0.1  videomasturbation.net
127.0.0.1  www.videomasturbation.net
# [ESTDOMAINS via Jack Anderson]
127.0.0.1  cruise-sex.com
127.0.0.1  naked-adult.net #[Trojan.Codec]
127.0.0.1  pornoplus.net
127.0.0.1  pornorelated.com
127.0.0.1  porno-want.com
127.0.0.1  sexy-drive.net #[Trojan.Codec]
127.0.0.1  the-adult.com
# [ESTDOMAINS via Jan Bernhard Loa]
127.0.0.1  adnserror.com
127.0.0.1  www.adnserror.com
127.0.0.1  esafetylist.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.esafetylist.com
127.0.0.1  esecuritynote.com
127.0.0.1  www.esecuritynote.com
# [ESTDOMAINS via Joha Kero]
127.0.0.1  allsecuritynotes.com #[SiteAdvisor.allsecuritynotes.com]
127.0.0.1  www.allsecuritynotes.com
127.0.0.1  asecuritypaper.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.asecuritypaper.com
127.0.0.1  ieprotectpage.com
127.0.0.1  www.ieprotectpage.com
127.0.0.1  secureiepage.com
127.0.0.1  www.secureiepage.com
# [ESTDOMAINS via John Saalfield][Angele Saada][Carl Feafter]
127.0.0.1  abcadult.net
127.0.0.1  adult-browse.com
127.0.0.1  click-adult.com
127.0.0.1  controladult.net
127.0.0.1  digitaladult.net
127.0.0.1  host-adult.net #[Trojan.Codec]
127.0.0.1  lineadult.net
127.0.0.1  mega-adult.net #[Trojan.Codec]
127.0.0.1  pornoextra.net
127.0.0.1  pornoshtorm.com
127.0.0.1  portaladult.net
127.0.0.1  virtualadult.net
# [ESTDOMAINS via Karol Anders]
127.0.0.1  bestpriceporn.com
127.0.0.1  www.bestpriceporn.com #[Spamdexing]
127.0.0.1  centerporn.net
127.0.0.1  coolbestporn.com
127.0.0.1  www.coolbestporn.com
127.0.0.1  drive-porn.com
127.0.0.1  funpornsite.com
127.0.0.1  www.funpornsite.com
127.0.0.1  funxxxporn.com #[Trojan.Codec]
127.0.0.1  land-porn.com
127.0.0.1  pornissex.com
127.0.0.1  www.pornissex.com
127.0.0.1  pornsexcafe.com
127.0.0.1  www.pornsexcafe.com
127.0.0.1  porntimeguide.com
127.0.0.1  www.porntimeguide.com #[Trojan.Codec]
127.0.0.1  pornxxxfilm.com
127.0.0.1  www.pornxxxfilm.com
127.0.0.1  relatedporn.net
127.0.0.1  superliveporn.com
127.0.0.1  www.superliveporn.com
127.0.0.1  superporncity.com
127.0.0.1  www.superporncity.com
127.0.0.1  teenporntop.com
127.0.0.1  www.teenporntop.com
127.0.0.1  time-porn.net
127.0.0.1  usbestporn.com
127.0.0.1  www.usbestporn.com
127.0.0.1  use-porn.com
127.0.0.1  want-porn.net
# [ESTDOMAINS via Lacky Ventures]
127.0.0.1  here4search.biz
127.0.0.1  smart-security.biz #[Trojan.Nebuler]
# [ESTDOMAINS via Lars Philip Svensson]
127.0.0.1  dailypornvids.net
127.0.0.1  www.dailypornvids.net
# [ESTDOMAINS via Leonard Podanowski]
127.0.0.1  porn-abc.com
127.0.0.1  pornabout.com
127.0.0.1  porn-contact.com #[Trojan.Codec]
127.0.0.1  porn-group.net
127.0.0.1  pornname.net
127.0.0.1  porn-plus.net
127.0.0.1  porn-power.net
127.0.0.1  porn-room.net
# [ESTDOMAINS via Lesli Kravik]
127.0.0.1  atrueprotection.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.atrueprotection.com
127.0.0.1  eprotectionline.com
127.0.0.1  www.eprotectionline.com
127.0.0.1  iesecuritytool.com
127.0.0.1  www.iesecuritytool.com
# [ESTDOMAINS via MakeMeSearch]
127.0.0.1  awmdabest.com
127.0.0.1  www.awmdabest.com #[SunBelt.Awmdabest]
127.0.0.1  makemesearch.com #[vip-se.com][Sunbelt.Tubby.MakeMeSearch]
127.0.0.1  www.makemesearch.com #[Parasite.Tubby][Parked?]
127.0.0.1  vip-se.com
127.0.0.1  www.vip-se.com
# [ESTDOMAINS via Mario Maxime][NetVids ltd][Videoscash]
127.0.0.1  bigvideosonline.com
127.0.0.1  www.bigvideosonline.com
127.0.0.1  todaysfreevideo.com
127.0.0.1  www.todaysfreevideo.com
# [ESTDOMAINS via Martin Adriano]
127.0.0.1  estserv01.com
127.0.0.1  www.estserv01.com
127.0.0.1  qnavigate.com #[SiteAdvisor.qnavigate.com]
127.0.0.1  www.qnavigate.com
# [ESTDOMAINS via Michael Bregnbak]
127.0.0.1  asecureboard.com
127.0.0.1  www.asecureboard.com
127.0.0.1  iesafetypage.com
127.0.0.1  www.iesafetypage.com
127.0.0.1  safetyhall.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.safetyhall.com
127.0.0.1  warningiepage.com
127.0.0.1  www.warningiepage.com
# [ESTDOMAINS via Mike James Group]
127.0.0.1  www.alltopus.com #[IFrame.Exploit]
127.0.0.1  asianxxxx.net
127.0.0.1  bbwlands.com
127.0.0.1  www.bbwlands.com #[Google.Warning]
127.0.0.1  bighugecocks.net #[Malicious.Links]
127.0.0.1  www.bighugecocks.net
127.0.0.1  bigtits4you.net
127.0.0.1  boobsfree.info #[Google.Warning]
127.0.0.1  dirtystockings.net #[Javascript.Exploit]
127.0.0.1  easiestgals.com
127.0.0.1  www.easiestgals.com
127.0.0.1  easygay.net
127.0.0.1  www.easygay.net
127.0.0.1  easylesbians.net #[IFrame.Exploit]
127.0.0.1  easytoons.net
127.0.0.1  ericsgirls.net
127.0.0.1  erotica2sex.com
127.0.0.1  exoticpornstar.info
127.0.0.1  femdomgirls.info #[Javascript.Exploit]
127.0.0.1  www.femdomgirls.info
127.0.0.1  forfat.net
127.0.0.1  fuckingasians.org
127.0.0.1  fuckingsluts.org
127.0.0.1  fuckladies.net
127.0.0.1  www.fuckladies.net
127.0.0.1  fuckthisteen.info
127.0.0.1  good-porn.org
127.0.0.1  happyadult.net #[Google.Warning]
127.0.0.1  www.happyadult.net
127.0.0.1  humpthisass.info
127.0.0.1  holyvoyeur.com
127.0.0.1  www.hotbigmelons.com
127.0.0.1  hotsvoyeur.com
127.0.0.1  hugecumshot.net #[SiteAdvisor.hugecumshot.net]
127.0.0.1  jokescartoons.info
127.0.0.1  lesbossex.org
127.0.0.1  www.lesbossex.org
127.0.0.1  likecumshots.info
127.0.0.1  mashaporn.com
127.0.0.1  mikesporn.org
127.0.0.1  momsexy.org #[Google.Warning]
127.0.0.1  mybigblackcock.org
127.0.0.1  mybigfat.net
127.0.0.1  mybitches.org
127.0.0.1  nakedgay.org
127.0.0.1  natashaporn.com
127.0.0.1  nexpussy.net
127.0.0.1  nextsex.org
127.0.0.1  niceerotica.com
127.0.0.1  nicehentai.net
127.0.0.1  nicepanties.net
127.0.0.1  nicetgps.com
127.0.0.1  www.nicetgps.com
127.0.0.1  nicewomen.org
127.0.0.1  nudeasian.biz
127.0.0.1  nudegay.info
127.0.0.1  onlyhotporn.net
127.0.0.1  pornochick.net
127.0.0.1  pornogals.org
127.0.0.1  pornoguns.com
127.0.0.1  www.pornoguns.com #[Google.Warning]
127.0.0.1  pornoheros.com
127.0.0.1  prettybutts.net
127.0.0.1  www.prettybutts.net
127.0.0.1  prettylesbos.net
127.0.0.1  rareporn.net
127.0.0.1  img.rareporn.net
127.0.0.1  www2.rareporn.net
127.0.0.1  www.rareporn.net
127.0.0.1  sexneeds.org
127.0.0.1  sexxxpornstars.com
127.0.0.1  sexyunlimited.net
127.0.0.1  www.sexyunlimited.net
127.0.0.1  shemales4u.info
127.0.0.1  shemalesnudes.com
127.0.0.1  shemalesocean.com
127.0.0.1  stockingsgalore.info
127.0.0.1  suckbigdicks.net
127.0.0.1  www.suckbigdicks.net
127.0.0.1  thebestadult.org
127.0.0.1  thehottestmoms.com
127.0.0.1  unrealsex.net
127.0.0.1  www.unrealsex.net
127.0.0.1  veryhotchicks.net
127.0.0.1  www.veryhotchicks.net
127.0.0.1  veryhotsex.org
127.0.0.1  voyeurdorms.info
127.0.0.1  welovepussy.net
127.0.0.1  wifesland.org
127.0.0.1  wowasses.com
127.0.0.1  www.wowasses.com
127.0.0.1  xxxsexnow.net
127.0.0.1  yoursgirls.com
127.0.0.1  yourpornstars.net
127.0.0.1  yoursluts.net
# [ESTDOMAINS via Nelroy LTD Group]
127.0.0.1  adultidate.com
127.0.0.1  www.adultidate.com
127.0.0.1  advancedfixer.com
127.0.0.1  get.adwarebazooka.com
127.0.0.1  www.adwarebazooka.com #[Rogue/Suspect]
127.0.0.1  www.adwaredelete.com #[Downloader-ACZ][Rogue/Suspect][StartPage-IF]
127.0.0.1  get.adwarepunisher.com #[Rogue/Suspect][SiteAdvisor.adwarepunisher.com]
127.0.0.1  www.adwarepunisher.com
127.0.0.1  antispyguide.com
127.0.0.1  www.antispy-products.com
127.0.0.1  www.awmteam.com
127.0.0.1  www.hitsdriving.com
127.0.0.1  get.hitvirus.com #[Win32/Adware.HitVirus]
127.0.0.1  help.hitvirus.com
127.0.0.1  support.hitvirus.com
127.0.0.1  www.hitvirus.com #[SiteAdvisor.hitvirus.com][Rogue/Suspect]
127.0.0.1  klikadvertising.com #[Webhelper.CWS List]
127.0.0.1  klik.klikadvertising.com
127.0.0.1  klikdoctor.com
127.0.0.1  www.klikdoctor.com
127.0.0.1  klikfeed.com
127.0.0.1  xml.klikfeed.com
127.0.0.1  www.klikfeed.com
127.0.0.1  www.klikrevenue.com
127.0.0.1  kliksoftware.com
127.0.0.1  www.kliksoftware.com
127.0.0.1  klikvip.com
127.0.0.1  xml2.klikvip.com
127.0.0.1  www.klikvip.com
127.0.0.1  www.nelroyltd.com
127.0.0.1  get.remedyantispy.com #[Rogue/Suspect]
127.0.0.1  www.remedyantispy.com
127.0.0.1  seekforweb.com
127.0.0.1  www.skibill.com #[SiteAdvisor.skibill.com]
127.0.0.1  get.spyanalyst.com
127.0.0.1  www.spyanalyst.com #[Rogue/Suspect]
127.0.0.1  get.spyiblock.com
127.0.0.1  www.spyiblock.com #[Rogue/Suspect]
127.0.0.1  spyofficer.com
127.0.0.1  get.spyofficer.com
127.0.0.1  www.spyofficer.com #[Rogue/Suspect]
127.0.0.1  thespyguard.com
127.0.0.1  get.thespyguard.com #[Rogue/Suspect]
127.0.0.1  www.thespyguard.com #[eTrust.Win32/Puper][McAfee.StartPage-IR]
127.0.0.1  winfixtools.com
# [ESTDOMAINS via Netdirekt E.k]
127.0.0.1  kwej.info
127.0.0.1  mnsj.info
127.0.0.1  mwbb.info
127.0.0.1  ovxz.info #[Spamdexing]
127.0.0.1  pokb.info
127.0.0.1  sjkl.info #[Javascript.Exploit]
127.0.0.1  vioh.info
127.0.0.1  xvcc.info #[Javascript.Exploit]
# [ESTDOMAINS via Nigel Ottman]
127.0.0.1  hotelcodec.com #[Trojan.Win32.DNSChanger.jc][server down?]
127.0.0.1  www.hotelcodec.com
127.0.0.1  totalcodec.com #[server down?]
127.0.0.1  www.totalcodec.com
127.0.0.1  yourcodec.com
127.0.0.1  www.yourcodec.com
# [ESTDOMAINS via NuNu][Inter Surprise]
127.0.0.1  1800taxfree.com #[VBS/Exploit.Phel.A]
127.0.0.1  700xxx.com
127.0.0.1  www.700xxx.com
127.0.0.1  alphaerotica.com
127.0.0.1  capitalhardcores.com
127.0.0.1  listincestsites.com #[StartPage-AU]
# [ESTDOMAINS via Oleg Izmailov]
127.0.0.1  search-end.com
127.0.0.1  search4www.net
127.0.0.1  searchinwww.net
# [ESTDOMAINS via Pant Co][Painter Co]
127.0.0.1  777mp3.com
127.0.0.1  a7p7.com
127.0.0.1  axespyware.com
127.0.0.1  www.axespyware.com
127.0.0.1  lalasearch.com
127.0.0.1  www.lalasearch.com
127.0.0.1  mp3traffic.net
127.0.0.1  online-casino-searcher.com #[McAfee.Painter]
127.0.0.1  painterppc.com
127.0.0.1  www.painterppc.com
127.0.0.1  painterdialer.com
127.0.0.1  www.painterdialer.com
127.0.0.1  paintertraffic.com
127.0.0.1  pindqas.com
127.0.0.1  pizzahunters.com
127.0.0.1  razespyware.net #[Downloader-ACZ][SiteAdvisor.razespyware.net]
127.0.0.1  get.razespyware.net #[Win32/Adware.HitVirus][ADW_SPYRAZE.A]
127.0.0.1  help.razespyware.net
127.0.0.1  www.razespyware.net #[Rogue/Suspect][SunBelt.RazeSpyware]
127.0.0.1  sertullo.com #[W32/Agent.ATIW.dropper]
127.0.0.1  sharpspyware.com #[Trojan.Agent.16]
127.0.0.1  www.sharpspyware.com
127.0.0.1  www.spywaredollars.com
# [ESTDOMAINS via Paul Godbee]
127.0.0.1  about-porn.com
127.0.0.1  contactporn.com
127.0.0.1  driveporn.com
127.0.0.1  look-porn.com
127.0.0.1  party-porn.com #[Trojan.Codec]
127.0.0.1  play-porn.com
127.0.0.1  www.play-porn.com
127.0.0.1  plus-porn.com
127.0.0.1  porn-look.com
127.0.0.1  porn-name.com
127.0.0.1  porn-www.com
127.0.0.1  relatedporn.com
127.0.0.1  serviceporn.com
# [ESTDOMAINS Paul Goodrich]
127.0.0.1  custom-sex.com
127.0.0.1  estatesex.com
127.0.0.1  part-sex.com
127.0.0.1  pleasure-sex.com #[Trojan.Codec]
127.0.0.1  porn-cruise.com
127.0.0.1  porn-sea.com
127.0.0.1  review-sex.com
127.0.0.1  service-sex.com
127.0.0.1  sex-other.com
127.0.0.1  sexother.com
127.0.0.1  time-sex.com
127.0.0.1  try-sex.com
# [ESTDOMAINS via Phil Andersen]
127.0.0.1  asecuresource.com
127.0.0.1  www.asecuresource.com
127.0.0.1  asecuretool.com
127.0.0.1  www.asecuretool.com
127.0.0.1  bnmgate.com #[Trojan.Zlob.M]
127.0.0.1  www.bnmgate.com
127.0.0.1  entertainclicks.com
127.0.0.1  www.entertainclicks.com
127.0.0.1  vzgate.com
127.0.0.1  www.vzgate.com
127.0.0.1  zaqgate.com
127.0.0.1  www.zaqgate.com
# [ESTDOMAINS via Pizdataya Compania][Wildcard DNS]
127.0.0.1  allteenmodel.com
127.0.0.1  www.allteenmodel.com
127.0.0.1  coolteenspage.com #[teens-co.com]
127.0.0.1  www.coolteenspage.com #[Trojan.Codec]
127.0.0.1  coolteenpussy.com
127.0.0.1  www.coolteenpussy.com
127.0.0.1  sexiw.com
127.0.0.1  sexlt.com
127.0.0.1  sexpu.com
127.0.0.1  sexyyoungpics.com
127.0.0.1  www.sexyyoungpics.com
127.0.0.1  somesexpics.com
127.0.0.1  www.somesexpics.com
127.0.0.1  www.sweet4all.com
127.0.0.1  sweetschoolgirl.com
127.0.0.1  www.sweetschoolgirl.com
127.0.0.1  teenpussymania.com
127.0.0.1  www.teenpussymania.com #[Trojan.TrustedZone]
127.0.0.1  www.teensexualitypics.com
127.0.0.1  teensspace.com
127.0.0.1  thumbstower.com
127.0.0.1  www.thumbstower.com
127.0.0.1  wsexi.com
127.0.0.1  x-drugs.com
# [ESTDOMAINS via Privacyprotect.org]
127.0.0.1  2007postcards.com #[Win32/Nuwar.gen worm]
127.0.0.1  404dnserrors.com
127.0.0.1  www.404dnserrors.com
127.0.0.1  about-adult.net
127.0.0.1  www.about-adult.net
127.0.0.1  about-sexy.com #[Trojan.Codec]
127.0.0.1  www.about-sexy.com
127.0.0.1  aclearsecurity.com
127.0.0.1  www.aclearsecurity.com
127.0.0.1  activexobj.com
127.0.0.1  www.activexobj.com
127.0.0.1  aflgate.com
127.0.0.1  www.aflgate.com
127.0.0.1  allvideodirect.com
127.0.0.1  amediasource.com #[server down?]
127.0.0.1  www.amediasource.com
127.0.0.1  antispyzone.com #[Rogue/Suspect][Symantec.AntiSpyZone]
127.0.0.1  www.antispyzone.com #[Prevx1.AntiSpyZone]
127.0.0.1  apicpreview.com
127.0.0.1  www.apicpreview.com
127.0.0.1  apicturetool.com #[server down?]
127.0.0.1  www.apicturetool.com
127.0.0.1  aprotectionweb.com
127.0.0.1  www.aprotectionweb.com
127.0.0.1  aprotectservice.com
127.0.0.1  www.aprotectservice.com
127.0.0.1  asafeguardinfo.com
127.0.0.1  www.asafeguardinfo.com
127.0.0.1  asafetyguide.com
127.0.0.1  www.asafetyguide.com
127.0.0.1  asafetyproduct.com
127.0.0.1  www.asafetyproduct.com
127.0.0.1  asafetyproject.com
127.0.0.1  www.asafetyproject.com
127.0.0.1  asafetytoolbar.com
127.0.0.1  www.asafetytoolbar.com
127.0.0.1  asecureadvice.com
127.0.0.1  www.asecureadvice.com
127.0.0.1  asecureguide.com
127.0.0.1  www.asecureguide.com
127.0.0.1  asecureservice.com
127.0.0.1  www.asecureservice.com
127.0.0.1  asecurezone.com
127.0.0.1  www.asecurezone.com
127.0.0.1  asecuritystuff.com
127.0.0.1  www.asecuritystuff.com
127.0.0.1  asecurityview.com
127.0.0.1  www.asecurityview.com
127.0.0.1  asiahomevideo.com
127.0.0.1  atrustedsoftware.com
127.0.0.1  www.atrustedsoftware.com
127.0.0.1  avideosurfer.com
127.0.0.1  www.avideosurfer.com
127.0.0.1  bestfuckvids.com #[Trojan.Codec]
127.0.0.1  www.bestfuckvids.com
127.0.0.1  bestskivideo.com
127.0.0.1  bestvideohouse.com
127.0.0.1  bestxxxmpegs.com #[Malicious.Links]
127.0.0.1  www.bestxxxmpegs.com
127.0.0.1  www.britneyraped.com #[Malicious.Links]
127.0.0.1  bqgate.com
127.0.0.1  www.bqgate.com
127.0.0.1  center-sexy.net #[Trojan.Codec]
127.0.0.1  chillyvids.com
127.0.0.1  transsexualmovies.chillyvids.com #[Trojan.Codec]
127.0.0.1  uniform.chillyvids.com
127.0.0.1  www.chillyvids.com
127.0.0.1  codeads.com
127.0.0.1  contact-adult.net
127.0.0.1  www.contact-adult.net
127.0.0.1  dailyxvids.com
127.0.0.1  www.dailyxvids.com #[Trojan.Codec]
127.0.0.1  diocleaner.com
127.0.0.1  www.diocleaner.com
127.0.0.1  downloadpics.net #[Trojan.Codec]
127.0.0.1  www.drantispy.com #[Symantec.DrAntiSpy]
127.0.0.1  dvdsclip.com
127.0.0.1  ecolorpostcards.com
127.0.0.1  enhancevideos.com #[Trojan.Codec][server down?]
127.0.0.1  www.enhancevideos.com
127.0.0.1  entersecuretool.com
127.0.0.1  www.entersecuretool.com
127.0.0.1  extasy-porn.net #[Trojan.Codec]
127.0.0.1  ddgate.com
127.0.0.1  www.ddgate.com
127.0.0.1  directmovs.com
127.0.0.1  www.directmovs.com
127.0.0.1  dxcodec.com
127.0.0.1  www.dxcodec.com
127.0.0.1  elitemovieszone.com #[Trojan.Codec]
127.0.0.1  expandvideo.com
127.0.0.1  www.expandvideo.com
127.0.0.1  www.eyrenet.com
127.0.0.1  www.favourlinks.com #[MVPS.Criteria]
127.0.0.1  www.freedutchmovies.com
127.0.0.1  freerealitympegs.com #[Trojan.Codec]
127.0.0.1  www.freerealitympegs.com #[Trojan.Virantix]
127.0.0.1  freewebpostcards.com
127.0.0.1  fuckergalleries.com
127.0.0.1  www.fuckergalleries.com #[IFrame.Exploit]
127.0.0.1  gateun.com
127.0.0.1  gateww.com
127.0.0.1  www.gateww.com
127.0.0.1  getmovieset.com
127.0.0.1  www.getmovieset.com
127.0.0.1  getpornvideoz.com #[Malicious.Links]
127.0.0.1  www.getpornvideoz.com
127.0.0.1  getsecuredtoday.com
127.0.0.1  www.getsecuredtoday.com
127.0.0.1  getvideosource.com
127.0.0.1  www.getvideosource.com
127.0.0.1  gooffhere.com
127.0.0.1  www.gooffhere.com
127.0.0.1  globoadvertising.net #[spyaway2007.com]
127.0.0.1  greatvideostore.com
127.0.0.1  group-adult.net
127.0.0.1  www.group-adult.net
127.0.0.1  guardtoolbar.com
127.0.0.1  www.guardtoolbar.com
127.0.0.1  gx-host.com #[Spamdexing]
127.0.0.1  helpporn.net
127.0.0.1  www.helpporn.net
127.0.0.1  hitscount.net #[MHTMLRedir.Exploit]
127.0.0.1  home-ticket.net
127.0.0.1  www.home-ticket.net
127.0.0.1  hqadultvideos.com #[Trojan.Codec]
127.0.0.1  www.hqadultvideos.com
127.0.0.1  hqfilmsxxx.com
127.0.0.1  www.hqfilmsxxx.com
127.0.0.1  hqstarvids.com
127.0.0.1  www.hqstarvids.com
127.0.0.1  hqthefilmsxxx.com #[Trojan.Codec]
127.0.0.1  www.hqthefilmsxxx.com
127.0.0.1  hqxxxtoo.com
127.0.0.1  hugefreevids.com #[Trojan.Codec]
127.0.0.1  www.hugefreevids.com
127.0.0.1  hugevideoszone.com #[Trojan.Codec]
127.0.0.1  www.hugevideoszone.com
127.0.0.1  imagescontrol.com #[TrojanDownloader:Win32/Zlob][server down?]
127.0.0.1  www.imagescontrol.com
127.0.0.1  imagesezine.com #[Trojan.Codec]
127.0.0.1  www.imagesezine.com
127.0.0.1  imagespecials.com
127.0.0.1  www.imagespecials.com
127.0.0.1  installobject.com #[TrojanDownloader:Win32/Zlob][server down?]
127.0.0.1  www.installobject.com
127.0.0.1  installmoviepro.com
127.0.0.1  www.installmoviepro.com
127.0.0.1  i-safetynet.net
127.0.0.1  iugate.com
127.0.0.1  jklgate.com #[McAfee.Puper.gen]
127.0.0.1  jokeonlineworld.com #[Win32/Nuwar.gen]
127.0.0.1  its.justcount.net
127.0.0.1  traff.justcount.net
127.0.0.1  keratomir2.biz #[spylocked.com]
127.0.0.1  www.keratomir2.biz
127.0.0.1  kozirodstwo.com
127.0.0.1  www.kozirodstwo.com #[Win32/TrojanDownloader.Small.NRS]
127.0.0.1  lbgate.com #[Trojan.Zlob.N]
127.0.0.1  www.lbgate.com
127.0.0.1  livewinupdates.com #[server down?]
127.0.0.1  www.livewinupdates.com
127.0.0.1  llgate.com
127.0.0.1  loadland.biz
127.0.0.1  look-adult.net
127.0.0.1  www.look-adult.net
127.0.0.1  mailfreepostcards.com
127.0.0.1  malwarepanacea.com
127.0.0.1  www.malwarepanacea.com
127.0.0.1  maxdoors.net
127.0.0.1  www.maxdoors.net
127.0.0.1  mediacodec2007.com
127.0.0.1  www.mediacodec2007.com
127.0.0.1  moreonlinesecurity.com
127.0.0.1  www.moreonlinesecurity.com
127.0.0.1  movietooklit.com
127.0.0.1  www.movietooklit.com
127.0.0.1  msiesettings.com
127.0.0.1  s74.msiesettings.com
127.0.0.1  s75.msiesettings.com #[Wildcard DNS]
127.0.0.1  s99.msiesettings.com
127.0.0.1  www.msiesettings.com
127.0.0.1  name-adult.net
127.0.0.1  www.name-adult.net
127.0.0.1  negas.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  newmediaobject.com
127.0.0.1  www.newmediaobject.com
127.0.0.1  newpornmovs.com
127.0.0.1  www.newpornmovs.com #[Malicious.Links]
127.0.0.1  nutsmpegs.com
127.0.0.1  www.nutsmpegs.com #[Trojan.Codec]
127.0.0.1  nvgate.com
127.0.0.1  www.nvgate.com
127.0.0.1  oegate.com
127.0.0.1  oigate.com
127.0.0.1  www.oigate.com
127.0.0.1  onlinevideopage.com
127.0.0.1  www.onlinevideopage.com #[Trojan.Codec][server down?]
127.0.0.1  onlinevideoset.com
127.0.0.1  www.onlinevideoset.com
127.0.0.1  onlyfreepornvideos.com #[Trojan.Codec]
127.0.0.1  www.onlyfreepornvideos.com
127.0.0.1  pageticket.com
127.0.0.1  www.pageticket.com
127.0.0.1  pageticket.net
127.0.0.1  www.pageticket.net
127.0.0.1  page-ticket.com
127.0.0.1  www.page-ticket.com #[Win32.PolyCrypt.b]
127.0.0.1  page-ticket.net
127.0.0.1  www.page-ticket.net
127.0.0.1  pagestickets.com
127.0.0.1  www.pagestickets.com
127.0.0.1  pcsecuritylab.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.pcsecuritylab.com
127.0.0.1  picturespool.com
127.0.0.1  www.picturespool.com
127.0.0.1  pleasure-adult.com
127.0.0.1  www.pleasure-adult.com
127.0.0.1  pleasure-porn.com
127.0.0.1  www.pleasure-porn.com
127.0.0.1  pogate.com
127.0.0.1  poratech.com #[Spamdexing]
127.0.0.1  porn-comp.com
127.0.0.1  www.porn-comp.com
127.0.0.1  porn-custom.com #[Trojan.Codec]
127.0.0.1  porn-look.net
127.0.0.1  porn-popular.com
127.0.0.1  www.porn-popular.com
127.0.0.1  porn-the.net #[Malicious.Links]
127.0.0.1  porntubesite.com #[Trojan.Codec]
127.0.0.1  www.porntubesite.com
127.0.0.1  porn-x-videos.com
127.0.0.1  www.porn-x-videos.com
127.0.0.1  postcardsbargain.com
127.0.0.1  poweradult.net
127.0.0.1  www.poweradult.net
127.0.0.1  practicaljokeonline.com
127.0.0.1  protectionclicks.com
127.0.0.1  www.protectionclicks.com
127.0.0.1  protectionfield.com
127.0.0.1  www.protectionfield.com
127.0.0.1  protectpage.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.protectpage.com
127.0.0.1  qzgate.com
127.0.0.1  realmoviezone.com #[Malicious.Links.Codec]
127.0.0.1  www.realmoviezone.com
127.0.0.1  repuc.info #[Javascript.Exploit]
127.0.0.1  rhgate.com
127.0.0.1  www.rhgate.com
127.0.0.1  ruswm.com #[Malicious.Links]
127.0.0.1  room-sexy.net #[Trojan.Codec]
127.0.0.1  safeguardbar.com
127.0.0.1  www.safeguardbar.com
127.0.0.1  safeinformations.com
127.0.0.1  www.safeinformations.com
127.0.0.1  securitysteps.com
127.0.0.1  www.securitysteps.com
127.0.0.1  service-porn.com
127.0.0.1  www.service-porn.com
127.0.0.1  setimagefile.com
127.0.0.1  www.setimagefile.com
127.0.0.1  sexy-look.com
127.0.0.1  sexy-popular.com #[Trojan.Codec]
127.0.0.1  spyhazard.com
127.0.0.1  www.spyhazard.com
127.0.0.1  streamule.com #[Trojan-Downloader.Win32.Zlob.and]
127.0.0.1  www.streamule.com
127.0.0.1  www.theillegalsite.com #[Trojan.Codec]
127.0.0.1  www.thumbsvids.com
127.0.0.1  topsexvidz.com
127.0.0.1  www.topsexvidz.com
127.0.0.1  topvidsonline.com #[Malicious.Links.Codec]
127.0.0.1  www.topvidsonline.com
127.0.0.1  traffdirect.com
127.0.0.1  try-adult.com #[Trojan.Codec]
127.0.0.1  useporn.net #[Trojan.Codec]
127.0.0.1  www.useporn.net
127.0.0.1  uniqueadult.com
127.0.0.1  www.uniqueadult.com
127.0.0.1  videoaccesscodec.com
127.0.0.1  www.videoaccesscodec.com
127.0.0.1  videossoftware.com #[server down?]
127.0.0.1  www.videossoftware.com
127.0.0.1  videotubemax.com
127.0.0.1  www.videotubemax.com
127.0.0.1  www.vineyteen.com
127.0.0.1  virusheal.com
127.0.0.1  www.virusheal.com
127.0.0.1  viruslocker.com
127.0.0.1  www.viruslocker.com
127.0.0.1  visit-adult.net
127.0.0.1  www.visit-adult.net
127.0.0.1  wayofprotection.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.wayofprotection.com
127.0.0.1  webdnserror.com
127.0.0.1  www.webdnserror.com
127.0.0.1  winupdatesserv.com #[Win32.Trojan-Downloader.VB.ASX][server down?]
127.0.0.1  www.winupdatesserv.com
127.0.0.1  win-ftp-plugin.info
127.0.0.1  www.win-ftp-plugin.info #[Trojan-Downloader.Win32.Zlob.and]
127.0.0.1  x-porngalleries.com #[Malicious.Links]
127.0.0.1  www.x-porngalleries.com
127.0.0.1  x-pornmoviez.com #[Trojan.Codec][MVPS.Criteria]
127.0.0.1  www.x-pornmoviez.com
127.0.0.1  x-pornvideoz.com
127.0.0.1  www.x-pornvideoz.com #[Trojan.Codec]
127.0.0.1  x-ratedclips.com #[Trojan.Codec]
127.0.0.1  www.x-ratedclips.com
127.0.0.1  xvgate.com
127.0.0.1  xvidscollection.com
127.0.0.1  www.xvidscollection.com
127.0.0.1  xxxvideopussy.com #[Malicious.Links]
127.0.0.1  www.xxxvideopussy.com
127.0.0.1  www.yegate.com
127.0.0.1  yourmoviessownload.com
127.0.0.1  www.yourtubeamp.com
127.0.0.1  ypka.com #[Spamdexing]
# [Privacyprotect.org via 85.255.121.77]
127.0.0.1  bdsmathome.info
127.0.0.1  best-pornostars-movies.info #[Spamdexing]
127.0.0.1  cross-nation-couples.org
127.0.0.1  girls-with-girls.info
127.0.0.1  girls-with-toys.info #[Malicious.Links.Codec]
127.0.0.1  incredible-asians-online.info
127.0.0.1  malayan-chicks.info
127.0.0.1  nice-females-dicked.org
127.0.0.1  pissing-skills-avi.info
127.0.0.1  trully-bigtits.info
127.0.0.1  uncensored-p0rn.info
127.0.0.1  xx-amateur-movies.org
127.0.0.1  www.xx-amateur-movies.org
# [ESTDOMAINS via Raxdev]
127.0.0.1  www.forexseek.com
127.0.0.1  www.giowanni.com
127.0.0.1  www.raxdev.com #[Adware.RaxSearch]
127.0.0.1  www.raxsearch.com #[McAfee.Spyware-RaxSrch]
127.0.0.1  www.scrsaver.com #[AdWare.Win32.RaxSearch.a]
127.0.0.1  www.xzgames.com
127.0.0.1  www.zippyinteractive.com #[searchadv.com]
# [ESTDOMAINS via Rickard Berg]
127.0.0.1  acegates.com
127.0.0.1  www.acegates.com
127.0.0.1  allsecuritylinks.com
127.0.0.1  www.allsecuritylinks.com
127.0.0.1  alltruesoftware.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.alltruesoftware.com
127.0.0.1  atotalsafety.com
127.0.0.1  www.atotalsafety.com
127.0.0.1  atruesecurity.com
127.0.0.1  www.atruesecurity.com
127.0.0.1  checkssecurity.com
127.0.0.1  www.checkssecurity.com
127.0.0.1  cleansoftwares.com #[Rogue/Suspect Affiliate.sites]
127.0.0.1  www.cleansoftwares.com
127.0.0.1  entertainingzone.com
127.0.0.1  www.entertainingzone.com
127.0.0.1  outgates.com
127.0.0.1  www.outgates.com
127.0.0.1  protectgates.com
127.0.0.1  www.protectgates.com
127.0.0.1  securityplugins.com
127.0.0.1  www.securityplugins.com
# [ESTDOMAINS via Robert Naidu][TCN Media]
127.0.0.1  adultvidsonly.com
127.0.0.1  www.adultvidsonly.com
127.0.0.1  chronoclips.com
127.0.0.1  www.chronoclips.com
127.0.0.1  freeeepornmovies.com #[MVPS.Criteria]
127.0.0.1  www.freeeepornmovies.com
127.0.0.1  dasistporn.com
127.0.0.1  www.dasistporn.com
127.0.0.1  free3xvids.com
127.0.0.1  www.free3xvids.com
127.0.0.1  kylemovies.com
127.0.0.1  www.kylemovies.com
127.0.0.1  lorixmovies.com
127.0.0.1  www.lorixmovies.com
127.0.0.1  masterpornvids.com
127.0.0.1  www.masterpornvids.com
127.0.0.1  megapornmovs.com
127.0.0.1  www.megapornmovs.com
127.0.0.1  megaxvids.com
127.0.0.1  www.megaxvids.com
127.0.0.1  moviesglam.com
127.0.0.1  www.moviesglam.com
127.0.0.1  razerporn.com
127.0.0.1  www.razerporn.com
127.0.0.1  reallyfreemovies.com
127.0.0.1  www.reallyfreemovies.com
127.0.0.1  steelpornmovies.com
127.0.0.1  www.steelpornmovies.com
127.0.0.1  superfreevids.com
127.0.0.1  www.superfreevids.com
127.0.0.1  tcnmedia.com
127.0.0.1  www.tcnmedia.com
127.0.0.1  winpornvids.com #[Trojan.Codec]
127.0.0.1  www.winpornvids.com
127.0.0.1  worldmovieporn.com
127.0.0.1  www.worldmovieporn.com
# [ESTDOMAINS via Slick Group][Max Inc]
127.0.0.1  golden-search.com #[Adware-Click]
127.0.0.1  gosearched.com
127.0.0.1  imlooking.net #[Trackware.SearchTerms]
127.0.0.1  www.imlooking.net
127.0.0.1  looking-for.net
127.0.0.1  smartsearchworld.com #[Adware.SmartSearch]
127.0.0.1  www.smartsearchworld.com
127.0.0.1  wwwhunter.net
# [ESTDOMAINS via SMP System]
127.0.0.1  chronomovies.com
127.0.0.1  www.chronomovies.com #[Trojan.Codec]
127.0.0.1  fovpornmovies.com
127.0.0.1  www.fovpornmovies.com
127.0.0.1  hvporn.com #[SiteAdvisor.hvporn.com]
127.0.0.1  www.hvporn.com
127.0.0.1  lotsofpornmovies.com
127.0.0.1  www.lotsofpornmovies.com #[Videoscash]
127.0.0.1  pornkingmovies.com
127.0.0.1  www.pornkingmovies.com #[Trojan.Codec]
# [ESTDOMAINS via SpyHeal LLC]
127.0.0.1  spyheal.biz
127.0.0.1  www.spyheal.biz
127.0.0.1  spyheal.com #[Win32/Adware.SpywareQuake][Rogue/Suspect]
127.0.0.1  www.spyheal.com #[Symantec.SpyHeal]
# [ESTDOMAINS via Stephen Middlebrook Group][Virpi Tervonen]
127.0.0.1  abuebu.com
127.0.0.1  babuinworld.com
127.0.0.1  bdsmpichunter.com
127.0.0.1  bigdirtymonkey.com
127.0.0.1  casinoonlineusa.com
127.0.0.1  chunkytgp.net
127.0.0.1  clicksagent.com
127.0.0.1  img.clicksagent.com
127.0.0.1  www.clicksagent.com
127.0.0.1  cliter.com
127.0.0.1  dirtybondagetgp.com
127.0.0.1  dirtychicken.com
127.0.0.1  dirtychicken.net
127.0.0.1  galleries.dirtychicken.net
127.0.0.1  drunkpichunter.com
127.0.0.1  drunksexygirls.com
127.0.0.1  ebonypichunter.com
127.0.0.1  fat-***-****.com
127.0.0.1  fat-women-pics.net
127.0.0.1  fatchickens.net
127.0.0.1  fatpichunter.com
127.0.0.1  freecitypictures.com
127.0.0.1  freegalleriessite.com
127.0.0.1  freegalleriesworld.com
127.0.0.1  freegalleryworld.com #[Malicious.Links]
127.0.0.1  www.freegalleryworld.com
127.0.0.1  freeinterracialgalleries.com
127.0.0.1  freejpgseries.com
127.0.0.1  freematureworld.com
127.0.0.1  freemegaporno.com #[Videoscash]
127.0.0.1  freepicturesfree.com
127.0.0.1  fuckherass.net
127.0.0.1  hairypichunter.com
127.0.0.1  hqgays.com
127.0.0.1  imagesmovies.com
127.0.0.1  indianpichunter.com
127.0.0.1  jpegindex.com
127.0.0.1  jpghunter.net
127.0.0.1  127.0.0.1  jpgsite.com #[Trojan.Codec]
127.0.0.1  kissherdick.com
127.0.0.1  largebabes.net
127.0.0.1  monkeycock.net
127.0.0.1  monkeyvids.net
127.0.0.1  moviesexserver.com #[Malicious Links]
127.0.0.1  natasjatgp.com
127.0.0.1  newfreegalleries.com
127.0.0.1  oldpichunter.com
127.0.0.1  onegaysex.com
127.0.0.1  onegranny.com
127.0.0.1  oneshemale.com
127.0.0.1  picturehunteronline.com
127.0.0.1  gallery.picturehunteronline.com
127.0.0.1  piggyworldtgp.com
127.0.0.1  piporno.com
127.0.0.1  pissingtgp.net
127.0.0.1  plumpchicks.net
127.0.0.1  plumpteens.net
127.0.0.1  realfatgirls.net
127.0.0.1  rubanners.com #[clicksagent.com]
127.0.0.1  img.ruclicks.com
127.0.0.1  www.ruclicks.com #[clicksagent.com]
127.0.0.1  russiantwinksecrets.com
127.0.0.1  sawenasex.com
127.0.0.1  spypichunter.com
127.0.0.1  srandel.com #[SiteAdvisor.srandel.com]
127.0.0.1  my.srandel.com
127.0.0.1  teen-gay-boys.net
127.0.0.1  thepregnantsex.com
127.0.0.1  trannypichunter.com
127.0.0.1  wildebonylovers.com
127.0.0.1  worldbestpics.com
127.0.0.1  yebalka.com
127.0.0.1  zetmovies.com
127.0.0.1  zmature.com
127.0.0.1  zhirok.com #[Spamdexing]
127.0.0.1  zuzik.net
127.0.0.1  zwebsearch.com
# [ESTDOMAINS via Thomas Price]
127.0.0.1  business-adult.com
127.0.0.1  comp-adult.com #[Trojan.Codec]
127.0.0.1  compadult.com
127.0.0.1  controladult.com
# [ESTDOMAINS via Tina Bruhn][William Frago]
127.0.0.1  about-adult.com
127.0.0.1  access-adult.com
127.0.0.1  browseadult.com
127.0.0.1  city-adult.com
127.0.0.1  driveadult.com
127.0.0.1  helpadult.com
127.0.0.1  key-adult.com
127.0.0.1  land-adult.com #[Trojan.Codec]
127.0.0.1  line-adult.com
127.0.0.1  lineadult.com
127.0.0.1  look-adult.com
127.0.0.1  network-adult.com #[JS/TrojanDownloader.Agent.AB]
127.0.0.1  play-adult.com
127.0.0.1  plus-adult.com
127.0.0.1  plusadult.com
127.0.0.1  portal-adult.com
127.0.0.1  power-adult.com
127.0.0.1  related-adult.com
127.0.0.1  relatedadult.com
127.0.0.1  scanadult.com
127.0.0.1  service-adult.com
127.0.0.1  serviceadult.com
127.0.0.1  timeadult.com
127.0.0.1  want-adult.com
127.0.0.1  wantadult.com
#[# [ESTDOMAINS via Tommy Larsen]
127.0.0.1  anerrordns.com
127.0.0.1  www.anerrordns.com
127.0.0.1  ie404error.com
127.0.0.1  www.ie404error.com
# [ESTDOMAINS via Upl Telecom S.r.o]
127.0.0.1  adultsonlyvids.com #[Trojan.Codec]
127.0.0.1  www.adultsonlyvids.com
127.0.0.1  asutra.org
127.0.0.1  bestpiu.info
127.0.0.1  chrsrv2.com #[Malicious Links]
127.0.0.1  freeallstar.info
127.0.0.1  greatsam.info
127.0.0.1  herowood.info
127.0.0.1  idoltrek.info
127.0.0.1  klhw.info
127.0.0.1  mixcomlines.info
127.0.0.1  netprovse.org
127.0.0.1  oeir.info #[Javascript.Exploit][Whois.Blacklisted]
127.0.0.1  oquw.info
127.0.0.1  piuttosto.info
127.0.0.1  supersamnet.info
127.0.0.1  superstarfire.info #[Trojan.Codec][Spamdexing]
127.0.0.1  universityedu.info #[Spamdexing]
127.0.0.1  westcomlines.info
127.0.0.1  yourpiu.info
# [ESTDOMAINS via Vasiliy Krolikov][Fast web solutions SRO]
127.0.0.1  mostimportant.org
127.0.0.1  procounter.biz #[W32/Downloader]
127.0.0.1  www.procounter.biz #[Troj/Agent-MD]
127.0.0.1  topnssearch.com #[Wildcard DNS]
127.0.0.1  12.topnssearch.com
127.0.0.1  26.topnssearch.com
127.0.0.1  60.topnssearch.com
# [ESTDOMAINS via Vasily Karasev][Hayter Merchants Group]
127.0.0.1  movies.allmoviegalleries.com
127.0.0.1  www.free-video-preview.com
127.0.0.1  gpisoft.com
127.0.0.1  www.gpisoft.com
# [ESTDOMAINS via Viktor Kron]
127.0.0.1  blackplanetsex.com #[Malicious.Links.Codec]
127.0.0.1  dexy.biz
127.0.0.1  www.dexy.biz
127.0.0.1  ebony-booty.biz
127.0.0.1  sergeantblack.com
# [ESTDOMAINS via Weddisign]
127.0.0.1  eoogl.com
127.0.0.1  egnomo.com #[Spamdexing]
127.0.0.1  iframebucks.com
# [ESTDOMAINS via WebTech Group]
127.0.0.1  onlinesecurityworld.com
127.0.0.1  www.onlinesecurityworld.com
127.0.0.1  onlinestability.com
127.0.0.1  www.onlinestability.com
# [ESTDOMAINS via Wuster Ltd Group][Evgeniy Lipec][Andre Julber]
127.0.0.1  100freegalls.com #[SiteAdvisor.100freegalls.com]
127.0.0.1  www.1001-search.com
127.0.0.1  1800-search.com #[Win32/TrojanDownloader.Delf.QY]
127.0.0.1  www.1800-search.com
127.0.0.1  2005-search.com #[Win32/TrojanClicker.Delf.CN]
127.0.0.1  www.2005-search.com
127.0.0.1  anali.org
127.0.0.1  bestgall.net #[Wildcard DNS]
127.0.0.1  www.bestgall.net
127.0.0.1  www.blowjobsdaily.com #[Javascript.Exploit]
127.0.0.1  www.cogidas.org #[IFrame.Exploit]
127.0.0.1  search-biz.info
127.0.0.1  search-biz.org
127.0.0.1  search-and-more.net
127.0.0.1  search-buy.biz
127.0.0.1  search-buy.info
127.0.0.1  search-buy.net
127.0.0.1  search-buy.org
127.0.0.1  search-club.net
127.0.0.1  search-free.net
127.0.0.1  search-free.org
127.0.0.1  search-galaxy.biz
# [ESTDOMAINS via ZAO Enisej][SE-Cash][Colin Drury]
127.0.0.1  colinsdialer.com 
127.0.0.1  www.colinsdialer.com
127.0.0.1  free-nylon-porn.com #[searchmeup.com]
127.0.0.1  freematureporn.org
127.0.0.1  www.freematureporn.org #[klikfeed.com]
127.0.0.1  www.mature-shop.com
127.0.0.1  www.topmatureporn.org
127.0.0.1  webse-arch.com
127.0.0.1  img.webse-arch.com
127.0.0.1  xml.webse-arch.com
# [Esthost via Mike Steel]
127.0.0.1  www.fetish-pix.com
127.0.0.1  www.mybans.com
# [Estico]
127.0.0.1  adultgambling.org #[ADW_MSNLIST.B]
127.0.0.1  www.adultgambling.org
127.0.0.1  adultsgames.net #[ADW_MSNLIST.B]
127.0.0.1  www.adwarecleaner.net #[findspyware.net]
127.0.0.1  www.adwareuninstall.net #[adultgambling.org]
127.0.0.1  allspyremover.com
127.0.0.1  allspyremover.net
127.0.0.1  bitchesonline.net
127.0.0.1  www.bitchesonline.net
127.0.0.1  www.cleanbrowser.org
127.0.0.1  www.cleanyourpc.net #[findspyware.net]
127.0.0.1  datingwcats.com
127.0.0.1  www.ultraload.net #[MHTMLRedir.Exploit]
# [eventures NV][Netthink Media]
127.0.0.1  www.bloghotspot.com
127.0.0.1  direct.combocash.com
127.0.0.1  www.eventuresnv.com
127.0.0.1  findwhatevernow.com #[ADW_FWNTOOLBAR.A]
127.0.0.1  search.findwhatevernow.com
127.0.0.1  www.findwhatevernow.com #[StartPage-FK]
127.0.0.1  direct.nastychannels.com
127.0.0.1  exits.nastychannels.com
127.0.0.1  www.nastychannels.com
# [Evolution World Wide Limited]
127.0.0.1  ads.dropspam.com #[HJTH.IEPlugin][server down.all]
127.0.0.1  my.dropspam.com
127.0.0.1  mysearch.dropspam.com #[McAfee.Adware-DropSpam]
127.0.0.1  sidesearch.dropspam.com
127.0.0.1  www.dropspam.com #[PcTools.DropSpam ToolBar]
# [eXact Advertising LLC][Innovation Interactive][360i LLC]
127.0.0.1  ct.360i.com #[McAfee.Cookie-360i][Panda.Spyware:Cookie/360i]
127.0.0.1  bargain-buddy.net #[Adware.BargainBuddy]
127.0.0.1  download.bargain-buddy.net #[Adware.IEHost][TROJ_DLOADER.MG]
127.0.0.1  service.bargain-buddy.net #[W32/BargainBuddy.AO.dropper]
127.0.0.1  service1.bargain-buddy.net #[McAfee.Adware-BB]
127.0.0.1  service2.bargain-buddy.net
127.0.0.1  service3.bargain-buddy.net
127.0.0.1  service4.bargain-buddy.net
127.0.0.1  service5.bargain-buddy.net
127.0.0.1  service6.bargain-buddy.net
127.0.0.1  service7.bargain-buddy.net
127.0.0.1  www.bargain-buddy.net #[AdWare.BargainBuddy.n]
127.0.0.1  www.benews.net
127.0.0.1  www.cashbackbuddy.com #[SunBelt.eXact.CashBack]
127.0.0.1  images.brainfox.com
127.0.0.1  search.brainfox.com
127.0.0.1  www.brainfox.com
127.0.0.1  download.bullseye-network.com
127.0.0.1  offers.bullseye-network.com #[Kephyr.PUP]
127.0.0.1  service.bullseye-network.com
127.0.0.1  www.bullseye-network.com #[Adware.Bullseye]
127.0.0.1  www.bullseye-network.net
127.0.0.1  results.cafefind.net
127.0.0.1  www.dealbandit.com
127.0.0.1  www.exactadvertising.com
127.0.0.1  www.exact-advertising.com
127.0.0.1  search.exactmatches.com
127.0.0.1  www.exactmatches.com
127.0.0.1  exactsearch.net
127.0.0.1  ww3.exactsearch.net
127.0.0.1  www.exactsearch.net #[Adware.NaviSearch]
127.0.0.1  exactsearchbar.com #[Adware.Exactbar][SPYW_EXACTBAR.A]
127.0.0.1  checkin.exactsearchbar.com #[SiteAdvisor.exactsearchbar.com]
127.0.0.1  www.exactsearchbar.com #[Parasite.eXactSearch]
127.0.0.1  www.exitcity.com
127.0.0.1  www.fungamedownloads.com
127.0.0.1  www.funwebapps.com
127.0.0.1  www.instantnavigation.com
127.0.0.1  leadgenetwork.com
127.0.0.1  www.leadgenetwork.com
127.0.0.1  www.link-popularity.info
127.0.0.1  www.navisearch.net
127.0.0.1  track.searchignite.com
127.0.0.1  www.searchignite.com
127.0.0.1  www.searchfish.com
127.0.0.1  domain.siteparker.com
127.0.0.1  search.siteparker.com
127.0.0.1  ads.textplussolutions.com
127.0.0.1  www.xctrk.com #[SiteAdvisor.bargain-buddy.net]
127.0.0.1  www.yubilee.com
# [Experian Interactive][Thermo Media]
127.0.0.1  banners.affiliatefuel.com #[SpySweeper.Spy.Cookie]
127.0.0.1  r1.affiliatefuel.com
127.0.0.1  www.affiliatefuel.com #[McAfee.Cookie-Affiliatefuel]
127.0.0.1  aftrk.com
127.0.0.1  banners.aftrk.com
127.0.0.1  ads.roundads.com
# [Extreme-DM][Tracking Service]
127.0.0.1  extreme-dm.com #[SecuritySpace.WebBug]
127.0.0.1  e0.extreme-dm.com
127.0.0.1  e1.extreme-dm.com
127.0.0.1  nht-2.extreme-dm.com #[eXTReMe Non Public Tracker Code]
127.0.0.1  nht-3.extreme-dm.com
127.0.0.1  reports.extreme-dm.com
127.0.0.1  t.extreme-dm.com
127.0.0.1  t0.extreme-dm.com
127.0.0.1  t1.extreme-dm.com
127.0.0.1  u.extreme-dm.com
127.0.0.1  u0.extreme-dm.com
127.0.0.1  u1.extreme-dm.com #[SunBelt.Extreme-DM.com]
127.0.0.1  v.extreme-dm.com
127.0.0.1  v0.extreme-dm.com
127.0.0.1  v1.extreme-dm.com
127.0.0.1  w.extreme-dm.com
127.0.0.1  w0.extreme-dm.com
127.0.0.1  w1.extreme-dm.com
127.0.0.1  x3.extreme-dm.com
127.0.0.1  y.extreme-dm.com #[Tenebril.Tracking.Cookie]
127.0.0.1  y0.extreme-dm.com
127.0.0.1  y1.extreme-dm.com
127.0.0.1  z.extreme-dm.com
127.0.0.1  z0.extreme-dm.com
127.0.0.1  z1.extreme-dm.com
# [Ezer Ratchaga][EzerNet]
127.0.0.1  www.adultfriendsearch.com
127.0.0.1  logo.affiliatebot.com
127.0.0.1  link.affiliatebot.com
127.0.0.1  affiliate.friendsearch.com
127.0.0.1  dating.friendsearch.com
127.0.0.1  partner.friendsearch.com
127.0.0.1  www.friendsearch.com
127.0.0.1  ads.free-banners.com
127.0.0.1  affiliate.free-banners.com
127.0.0.1  home.free-banners.com
127.0.0.1  www.free-banners.com
127.0.0.1  ads.freevisits.com
127.0.0.1  search.hotplugins.com
127.0.0.1  www.hotplugins.com
127.0.0.1  toolbar.push.com #[searchv2.dll]
# [Falk AdSolution][Falk eSolutions AG][DoubleClick]
127.0.0.1  a.as-eu.falkag.net
127.0.0.1  a.as-eu1.falkag.net
127.0.0.1  admin.as-eu.falkag.net
127.0.0.1  bw.as-eu.falkag.net
127.0.0.1  c.as-eu.falkag.net
127.0.0.1  data.as-eu.falkag.net
127.0.0.1  e.as-eu.falkag.net #[Ewido.TrackingCookie.Falkag]
127.0.0.1  f.as-eu.falkag.net
127.0.0.1  origin.as-eu.falkag.net
127.0.0.1  red.as-eu.falkag.net #[McAfee.Adware-Zeno]
127.0.0.1  red01.as-eu.falkag.net
127.0.0.1  sel.as-eu.falkag.net
127.0.0.1  a.as-test.falkag.net #[Panda.Spyware:Cookie/Falkag]
127.0.0.1  bw.as-test.falkag.net
127.0.0.1  red.as-test.falkag.net
127.0.0.1  sel.as-test.falkag.net
127.0.0.1  a.as-us.falkag.net #[SunBelt.as-us.falkag]
127.0.0.1  b.as-us.falkag.net
127.0.0.1  bw.as-us.falkag.net #[a1339.g.akamai.net]
127.0.0.1  c.as-us.falkag.net #[Tenebril.Tracking.Cookie]
127.0.0.1  data.as-us.falkag.net
127.0.0.1  e.as-us.falkag.net #[a1339.g.akamai.net]
127.0.0.1  origin.as-us.falkag.net
127.0.0.1  red.as-us.falkag.net
127.0.0.1  red01.as-us.falkag.net
127.0.0.1  s.as-us.falkag.net
127.0.0.1  sel.as-us.falkag.net
127.0.0.1  as1.falkag.de #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.falkag.de
127.0.0.1  ad1.adsolution.de
127.0.0.1  a.ads.t-online.de #[AdSolution-Website-Tag]
127.0.0.1  admin.ads.t-online.de
127.0.0.1  bw.ads.t-online.de
127.0.0.1  data.ads.t-online.de
127.0.0.1  homepage.t-online.de
127.0.0.1  red.ads.t-online.de
127.0.0.1  s.ads.t-online.de
127.0.0.1  toi.passul.t-online.de
127.0.0.1  count.passul.t-online.de
# [Farid Faryadi][Farid Farckili][Endi Streff]
127.0.0.1  813aw0nr01jsxfj374ca.com
127.0.0.1  adscontex.com #[TR/Dldr.Small.ddp.28]
127.0.0.1  www.adscontex.com
127.0.0.1  www.adsforsite.com
127.0.0.1  www.appzplanet.com #[AdWare.Win32.Underground]
127.0.0.1  www.fandl.net #[server down?]
127.0.0.1  www.finditanyway.com
127.0.0.1  www.freeserials.com #[Win32.Renos.az]
127.0.0.1  www.freeserials.net
127.0.0.1  www.googlecaches.com
127.0.0.1  www.liporn.com
127.0.0.1  www.mswindowssearch.com
127.0.0.1  trustcleaner.com #[AntiVir.ADSPY/UntrustCl.A.1]
127.0.0.1  www.trustcleaner.com #[Symantec.TrustCleaner]
127.0.0.1  clicks.trustclicks.com
127.0.0.1  dating.trustclicks.com
127.0.0.1  www.trustclicks.com
127.0.0.1  trustincash.com
127.0.0.1  soft.trustincash.com #[Trojan-Downloader.Win32.Small.ddx]
127.0.0.1  www.trustincash.com
127.0.0.1  trustinsearch.com #[813aw0nr01jsxfj374ca.com]
127.0.0.1  assistant.trustinsearch.com
127.0.0.1  toolbar.trustinsearch.com
127.0.0.1  www.trustinsearch.com #[AdWare.Win32.Azesearch.h]
# [FastLook Group]
127.0.0.1  www.fastlook.net #[McAfee.StartPage-EK][Adware.FastLook][Parked?]
127.0.0.1  pages2start.com
127.0.0.1  www.pages2start.com #[McAfee.StartPage-AY][Parked?]
127.0.0.1  www.search-directories.com #[Parked?]
127.0.0.1  searchsuggestions.com
127.0.0.1  www.searchsuggestions.com #[Parked?]
# [Feeble Minded Productions][Sanford Wallace]
127.0.0.1  www.freevegasclubs.com
# [First Cash Reserve][IBIS LLC][Xacti Group]
127.0.0.1  www.404-errorpage.com
127.0.0.1  as.adwave.com #[Parasite.HuntBar][Panda.Adware/WinTools]
127.0.0.1  search.adwave.com #[McAfee.Adware-IEHost]
127.0.0.1  sr.adwave.com
127.0.0.1  www.bestjobsguide.com
127.0.0.1  www.bestphonesguide.com
127.0.0.1  www.funscreensaverscentral.com
127.0.0.1  download.funutilities.com
127.0.0.1  screensavers.funutilities.com
127.0.0.1  ws.funutilities.com
127.0.0.1  www.funutilities.com #[SiteAdvisor.funutilities.com]
127.0.0.1  www.globalwebpass.com
127.0.0.1  www.ibis.com
127.0.0.1  www.ibisit.com #[SiteAdvisor.ibisit.com]
127.0.0.1  www.ibis.cz
127.0.0.1  www.myscreensaverlink.com
127.0.0.1  www.spyterm.com
127.0.0.1  www.spywarelinkcentral.com
127.0.0.1  adserver.trafficsyndicate.com #[SunBelt.trafficsyndicate.com]
127.0.0.1  distribution.trafficsyndicate.com #[server down?]
127.0.0.1  dst.trafficsyndicate.com #[Parasite.HuntBar][server down?]
127.0.0.1  search.trafficsyndicate.com
127.0.0.1  xml.trafficsyndicate.com
127.0.0.1  xml2.trafficsyndicate.com
127.0.0.1  ads.crawler.com
127.0.0.1  cfg.crawler.com #[SiteAdvisor.funutilities.com]
127.0.0.1  demo.crawler.com
127.0.0.1  dnl.crawler.com #[NOD32.Win32/Adware.Crawler]
127.0.0.1  download.crawler.com #[AdWare.Win32.Crawler.b]
127.0.0.1  i30.crawler.com
127.0.0.1  is1.crawler.com
127.0.0.1  mb.crawler.com #[F-Secure.Crawler Toolbar]
127.0.0.1  portal.crawler.com #[McAfee.Adware-CTBar]
127.0.0.1  ranking.crawler.com
127.0.0.1  rs.crawler.com
127.0.0.1  spell.crawler.com
127.0.0.1  ws.crawler.com #[ZoneLabs.Win32.AdWare.Crawler.a]
127.0.0.1  www.crawler.com #[SiteAdvisor.crawler.com]
127.0.0.1  senkypl.com
127.0.0.1  websearch.com #[Adware.Huntbar][TRUSTe.Violator]
127.0.0.1  download.websearch.com #[SPYW_WEBSEARCH.A][Downloader-TH]
127.0.0.1  games.websearch.com
127.0.0.1  is1.websearch.com
127.0.0.1  is2.websearch.com
127.0.0.1  ranking.websearch.com
127.0.0.1  rs.websearch.com
127.0.0.1  skins.websearch.com
127.0.0.1  sr.websearch.com
127.0.0.1  ws.websearch.com
127.0.0.1  www.websearch.com.au
127.0.0.1  websearch.co.uk
127.0.0.1  www.websearch.com #[WebSearch Toolbar.Emailplug][ADW_DOWNLOADER.E]
127.0.0.1  www.websearch.net
127.0.0.1  dnl.websecurityguard.com
127.0.0.1  www.websecurityguard.com #[SiteAdvisor.websecurityguard.com]
127.0.0.1  win-tools.com #[ADW_WSEARCH.109]
127.0.0.1  www.win-tools.com
# [First Consulting]
127.0.0.1  home.searchwords.com #[eTrust.AdRoad.Cpr]
127.0.0.1  info.searchwords.com #[SiteAdvisor.searchwords.com]
127.0.0.1  weather.searchwords.com #[McAfee.Adware-Searchwords]
127.0.0.1  www.searchwords.com #[Adware.SearchWords]
127.0.0.1  quasar.sitegauge.com
# [Flashpoint Media][Parasite.FlashTrack]
127.0.0.1  a.flashpoint.bm
127.0.0.1  c.flashpoint.bm
127.0.0.1  www.flashpoint.bm
127.0.0.1  www.flashpointmediagroup.com
127.0.0.1  www.flashpointmodelsearch.com
127.0.0.1  flashtrack.net #[IE-SpyAd]
127.0.0.1  ads.flashtrack.net #[Adware.Flashtrack.B]
127.0.0.1  coreg.flashtrack.net
127.0.0.1  xml.flashtrack.net #[VPP Technologies]
127.0.0.1  www.flashtrack.net #[Adware.FlashEnhancer]
127.0.0.1  config.broadcastpc.tv #[TROJ_RVP.E]
127.0.0.1  report.broadcastpc.tv #[AdvWare.Broadcap.a]
127.0.0.1  www.broadcastpc.tv #[Adware.Broadcastpc]
127.0.0.1  www.downaload.com
# [Focus Interactive / InterActiveCorp][Ask Jeeves, Inc][benedelman.org.askjeeves]
127.0.0.1  buddies.funbuddyicons.com
127.0.0.1  www.funbuddyicons.com #[SunBelt.FunWebProducts]
127.0.0.1  download.funwebproducts.com #[AdWare.Win32.FunWeb.e]
127.0.0.1  www.funwebproducts.com #[Adware.Bundler.Funwebproducts.M]
127.0.0.1  www.historyswatter.com
127.0.0.1  ads.iwon.com
127.0.0.1  c4.iwon.com
127.0.0.1  cc.iwon.com #[iWon Progressive Counter]
127.0.0.1  docs1.iwon.com
127.0.0.1  image.i1img.com
127.0.0.1  my.iwon.com
127.0.0.1  plus.iwon.com
127.0.0.1  prizemachine.games.iwon.com
127.0.0.1  search.iwon.com
127.0.0.1  searchassistant.iwon.com
127.0.0.1  www1.iwon.com #[ADW_IWON.B]
127.0.0.1  bar.mytotalsearch.com
127.0.0.1  www.mytotalsearch.com
127.0.0.1  mn.myquicksearch.com
127.0.0.1  mr.myquicksearch.com
127.0.0.1  www.myquicksearch.com #[SunBelt.MyQuickSearch Search Assistant]
127.0.0.1  ak.maxserving.com #[Tenebril.Tracking.Cookie][a698.g.akamai.net]
127.0.0.1  c4.maxserving.com #[SpySweeper.Spy.Cookie]
127.0.0.1  img.maxserving.com
127.0.0.1  sc4.maxserving.com
127.0.0.1  myglobalsearch.com
127.0.0.1  cfg.myglobalsearch.com
127.0.0.1  www.myglobalsearch.com #[Ewido.Spyware.MyWebSearch.MyGlobalSearch]
127.0.0.1  c4.mysearch.com #[eTrust.MySearch][ADW_MYSEARCH.202]
127.0.0.1  www.mysearch.com #[ADW_MIWAY.B][ADWARE_BHO_MYWAY]
127.0.0.1  help.mysearch.com #[SunBelt.My Search Bar][Ewido.Spyware.MySearch]
127.0.0.1  mywebsearch.com #[McAfee.Adware-MyWebSearch]
127.0.0.1  bar.mywebsearch.com #[ADW_MYWEB.A][eTrust.MyWebSearch Toolbar]
127.0.0.1  cfg.mywebsearch.com
127.0.0.1  download.mywebsearch.com #[ADW_WEBSEARCH.K]
127.0.0.1  edits.mywebsearch.com
127.0.0.1  search.mywebsearch.com #[Panda.Adware/MyWebSearch]
127.0.0.1  weatherbugbrowserbar.mywebsearch.com
127.0.0.1  www.mywebsearch.com #[Ewido.Spyware.MyWebSearch]
127.0.0.1  cm.myway.com #[Ewido.Spyware.MyWay][ADW_MIWAY.C]
127.0.0.1  utm.cursormania.com
127.0.0.1  utm.trk.cursormania.com
127.0.0.1  utm.trk.excite.com
127.0.0.1  utm.myfuncards.com
127.0.0.1  utm.trk.myfuncards.com
127.0.0.1  utm.trk.myway.com
127.0.0.1  utm.myway.com #[service.urchin.com]
127.0.0.1  utm.popswatter.com
127.0.0.1  utm.trk.popswatter.com
127.0.0.1  utm.popularscreensavers.com
127.0.0.1  utm.trk.popularscreensavers.com
127.0.0.1  utm.smileycentral.com
127.0.0.1  utm2.smileycentral.com
127.0.0.1  utm.trk.smileycentral.com
127.0.0.1  utmtrk2.smileycentral.com
127.0.0.1  utm.zwinky.com
127.0.0.1  utm.trk.zwinky.com
127.0.0.1  speedbar.myway.com #[ADW_MYSPEED.A][ADW_MIWAY.C]
127.0.0.1  cm.need2find.com #[Panda.adware/need2find]
127.0.0.1  ka.bar.need2find.com #[HJTH.Need2Find bar][McAfee.Adware-Need2Find]
127.0.0.1  kc.search.need2find.com #[mwave.AdWare.MySearch.e]
127.0.0.1  kz.js.need2find.com #[Ewido.Spyware.Need2Find]
127.0.0.1  kz.search.need2find.com #[altnet.com]
# [Focalex, Inc][Tracking Service]
127.0.0.1  focalex.com #[SiteAdvisor.focalex.com]
127.0.0.1  img.focalex.com
127.0.0.1  load.focalex.com
127.0.0.1  pluto.focalex.com
127.0.0.1  solutions.focalex.com
127.0.0.1  tafbar.focalex.com
127.0.0.1  tafmaster-p.focalex.com
127.0.0.1  tafmaster-s.focalex.com
127.0.0.1  tafmaster-t.focalex.com
127.0.0.1  tafmaster-v.focalex.com
127.0.0.1  tafmaster-v2.focalex.com
127.0.0.1  tafmaster-v3.focalex.com
127.0.0.1  tafmaster-v4.focalex.com
127.0.0.1  tafmaster-v5.focalex.com
127.0.0.1  tafmaster-v6.focalex.com
127.0.0.1  tafmaster-v7.focalex.com
127.0.0.1  tafmaster-v8.focalex.com
127.0.0.1  tafmaster-v9.focalex.com
127.0.0.1  tafmaster-v10.focalex.com
127.0.0.1  tafmaster-v11.focalex.com
127.0.0.1  tafmaster-v12.focalex.com
127.0.0.1  tafmaster-v14.focalex.com
127.0.0.1  tafmaster-v15.focalex.com
127.0.0.1  tafmaster-v16.focalex.com
127.0.0.1  thankyou.focalex.com
127.0.0.1  thankyou-v2.focalex.com
127.0.0.1  thankyou-v3.focalex.com
127.0.0.1  thankyou-v4.focalex.com
127.0.0.1  thankyou-v5.focalex.com
127.0.0.1  thankyou-v6.focalex.com
127.0.0.1  webgames.focalex.com
127.0.0.1  webgames-a.focalex.com
127.0.0.1  webgames-v1.focalex.com
127.0.0.1  tafbar.com #[Symantec.Spyware.TAFbar][SunBelt.Tafbar]
127.0.0.1  s.tafbar.com
127.0.0.1  www.tafbar.com #[ADW_TAFBAR.A]
127.0.0.1  tafmaster.com
127.0.0.1  image.tafmaster.com #[tafmaster-i.focalex.com]
127.0.0.1  public.tafmaster.com
127.0.0.1  www.tafmaster.com
# [Fordale Investment]
127.0.0.1  downloadware.net
127.0.0.1  www.downloadware.net #[eTrust.DownloadWare]
127.0.0.1  fordaleltd.com
127.0.0.1  config.fordaleltd.com
127.0.0.1  download.fordaleltd.com #[Adware.Dware]
127.0.0.1  www.fordaleltd.com
# [Fortunecity]
127.0.0.1  www.ampira.com 
127.0.0.1  ads.fortunecity.com #[SpySweeper.Spy.Cookie]
127.0.0.1  oascentral.fortunecity.com #[RealMedia]
127.0.0.1  www2.fortunecity.com #[SunBelt.FortuneCity.com]
127.0.0.1  ads.v3.com
# [Fox Interactive Media]
127.0.0.1  popups.ad-logics.com #[McAfee.Cookie-Ad-logics]
127.0.0.1  ads.americanidol.com
127.0.0.1  ads.euniverseads.com #[McAfee.Cookie-Euniverseads]
127.0.0.1  ms.euniverseads.com
127.0.0.1  ads.ign.com #[McAfee.Cookie-IGN]
127.0.0.1  de.ign.com
127.0.0.1  t.ign.com
127.0.0.1  tracker.ign.com
127.0.0.1  dartimg.intermix.com
127.0.0.1  de.imixserver.com
127.0.0.1  debnb.imixserver.com
127.0.0.1  debnt.imixserver.com
127.0.0.1  delb.imixserver.com
127.0.0.1  demr.imixserver.com
127.0.0.1  demr2.imixserver.com
127.0.0.1  depl.imixserver.com
127.0.0.1  depopen.imixserver.com
127.0.0.1  depopex.imixserver.com
127.0.0.1  desky.imixserver.com
127.0.0.1  desky2.imixserver.com
127.0.0.1  www.imixserver.com
127.0.0.1  ads.partner2profit.com
127.0.0.1  imp.partner2profit.com
127.0.0.1  www.partner2profit.com
127.0.0.1  a.photobucket.com #[photobkt.adbureau.net]
127.0.0.1  adserver.snowball.com
127.0.0.1  t.snowball.com
# [FreeMyName, LLC]
127.0.0.1  www.fmnmedia.com
127.0.0.1  www.fmn-media.com #[HJTH.FMN Media Web Advertiser]
127.0.0.1  www.freemyname.com
# [FullContext][Jutta Herdzin][SunBelt.Adw.FullContext.FChelp]
127.0.0.1  newads1.com
127.0.0.1  www.newads1.com
127.0.0.1  newads2.com
127.0.0.1  www.newads2.com
# [Fun-Lotto.com][ZQuest Media][Mermaid Consulting]
127.0.0.1  adpowerzone.com #[eTrust.SearchExplorerBar]
127.0.0.1  ads.adpowerzone.com
127.0.0.1  easy.adpowerzone.com
127.0.0.1  ss.adpowerzone.com
127.0.0.1  tb.adpowerzone.com #[McAfee.Adware-ExplBar]
127.0.0.1  tb-static.adpowerzone.com #[Adware.Websearch]
127.0.0.1  www.adpowerzone.com #[Adware.Searchexplorer]
127.0.0.1  www.alwaysfreealways.com #[Trojan.Win32.StartPage.yq]
127.0.0.1  servedby.headlinesandnews.com
127.0.0.1  adsby.uzoogle.com
127.0.0.1  games.uzoogle.com
127.0.0.1  www.uzoogle.com #[Win32/Zquest.A]
127.0.0.1  z-quest.com #[Adware.ZQuest]
127.0.0.1  ads.z-quest.com
127.0.0.1  www.z-quest.com #[McAfee.Zquest]
127.0.0.1  www.zquest.com
# [FunnyTaf Inc]
127.0.0.1  cards.cardfountain.com
127.0.0.1  cards.free.cardfountain.com
127.0.0.1  www.cardfountain.com
127.0.0.1  www.enmarketing.com
127.0.0.1  funnytaf.com #[SiteAdvisor.funnytaf.com]
127.0.0.1  mailer.funnytaf.com #[SiteAdvisor.trustyhound.net]
127.0.0.1  www.funnytaf.com
127.0.0.1  trustyhound.com #[SunBelt.TrustyHound]
127.0.0.1  www.trustyhound.com #[Spyware.TrustyHound]
# [Gabor Timis]
127.0.0.1  www.adult-screensavers.org #[NOD32.Win32/AdInstaller]
127.0.0.1  www.idolove.com #[Win32/AdInstaller][SiteAdvisor.idolove.com]
127.0.0.1  www.mylovecards.com #[Win32/AdInstaller]
# [Galt Technology][Website Solutions]
127.0.0.1  www.celebrity-wallpaper.com
127.0.0.1  www.daily1.com #[AdWare.Win32.SaveNow.bo]
127.0.0.1  www.funskins.com
127.0.0.1  www.galttech.com #[AdWare.Win32.FunWeb.e]
127.0.0.1  www.mp3yes.com #[SiteAdvisor.mp3yes.com]
127.0.0.1  www.my-free-ringtones.com
127.0.0.1  www.ordercd.com
127.0.0.1  www.rubberfaces.com #[SiteAdvisor.rubberfaces.com]
127.0.0.1  www.screensaverheaven.com #[Trojan.Muldrop.3051.A]
127.0.0.1  www.topscreensavers.com #[SiteAdvisor.galttech.com]
127.0.0.1  www.wallpaperworld.com
127.0.0.1  www.wrestling1.com
# [GeMius]
127.0.0.1  hit.gemius.pl #[McAfee.Cookie-Gemius]
127.0.0.1  activeby.hit.gemius.pl
127.0.0.1  ad.hit.gemius.pl
127.0.0.1  adclick.hit.gemius.pl
127.0.0.1  adlt.hit.gemius.pl
127.0.0.1  adnet.hit.gemius.pl
127.0.0.1  arbo.hit.gemius.pl
127.0.0.1  allegro.hit.gemius.pl
127.0.0.1  centrumcz.hit.gemius.pl
127.0.0.1  cz.hit.gemius.pl
127.0.0.1  gadk.hit.gemius.pl
127.0.0.1  gadnet.hit.gemius.pl
127.0.0.1  gail.hit.gemius.pl
127.0.0.1  gask.hit.gemius.pl
127.0.0.1  gdecz.hit.gemius.pl
127.0.0.1  hr.hit.gemius.pl
127.0.0.1  hu.hit.gemius.pl
127.0.0.1  idm.hit.gemius.pl
127.0.0.1  intao.hit.gemius.pl
127.0.0.1  interia.hit.gemius.pl
127.0.0.1  kon.hit.gemius.pl
127.0.0.1  lt.hit.gemius.pl
127.0.0.1  onet.hit.gemius.pl
127.0.0.1  opt.hit.gemius.pl
127.0.0.1  pro.hit.gemius.pl
127.0.0.1  seznam.hit.gemius.pl
127.0.0.1  spir.hit.gemius.pl
127.0.0.1  st.hit.gemius.pl
127.0.0.1  st1.hit.gemius.pl
127.0.0.1  std1.hit.gemius.pl #[SecuritySpace.WebBug]
127.0.0.1  stua.hit.gemius.pl
127.0.0.1  wp.hit.gemius.pl
127.0.0.1  home.hit.stat.pl
127.0.0.1  onet.hit.stat.pl
127.0.0.1  s1.hit.stat.pl
127.0.0.1  s2.hit.stat.pl
127.0.0.1  s3.hit.stat.pl
127.0.0.1  s4.hit.stat.pl
127.0.0.1  sisco.hit.stat.pl
127.0.0.1  www.stat.pl
# [Geo Targeted Banner System]
127.0.0.1  abum.axelsfun.com
127.0.0.1  banner1.axelsfun.com
127.0.0.1  banner2.axelsfun.com
127.0.0.1  banner3.axelsfun.com
127.0.0.1  bannerus1.axelsfun.com #[Wildcard DNS]
127.0.0.1  bannerus2.axelsfun.com
127.0.0.1  bannerus3.axelsfun.com
127.0.0.1  crazyshit.axelsfun.com
127.0.0.1  etology.axelsfun.com
127.0.0.1  etology1.axelsfun.com
127.0.0.1  horoxxx.axelsfun.com
127.0.0.1  mrwally.axelsfun.com
127.0.0.1  nastyrat.axelsfun.com
127.0.0.1  p138920c.axelsfun.com
127.0.0.1  p144924c.axelsfun.com
127.0.0.1  p165535.axelsfun.com
127.0.0.1  p171605.axelsfun.com
127.0.0.1  p174613c.axelsfun.com
127.0.0.1  p54883c.axelsfun.com
127.0.0.1  rknet.axelsfun.com
127.0.0.1  sexyfunn.axelsfun.com
127.0.0.1  spasmo.axelsfun.com
127.0.0.1  taxidriver.axelsfun.com
127.0.0.1  vasmedia.axelsfun.com
127.0.0.1  vogue007.axelsfun.com
127.0.0.1  xapster.axelsfun.com
# [Gigex, Inc]
127.0.0.1  gigex.com #[IE-SpyAd]
127.0.0.1  media.gigex.com #[HJTH.Gigex SpeedDelivery]
127.0.0.1  oascentral.gigex.com #[RealMedia]
127.0.0.1  www.gigex.com #[eTrust.Gigex SpeedDelivery]
# [Google Inc]
127.0.0.1  pagead.googlesyndication.com
127.0.0.1  pagead2.googlesyndication.com #[Google AdWords]
127.0.0.1  adservices.google.com
127.0.0.1  ssl.google-analytics.com #[urchinTracker]
127.0.0.1  www.google-analytics.com #[Google Analytics]
127.0.0.1  imageads.googleadservices.com #[Ewido.TrackingCookie.Googleadservices]
127.0.0.1  partner.googleadservices.com
127.0.0.1  www.googleadservices.com
127.0.0.1  apps5.oingo.com #[Microsoft.Typo-Patrol]
127.0.0.1  www.appliedsemantics.com
127.0.0.1  service.urchin.com #[Urchin Tracking Module]
# [Green-Acres Services][Tracking Service]
127.0.0.1  123count.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.123count.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.123stat.com
127.0.0.1  web-stat.com #[SpySweeper.Spy.Cookie]
127.0.0.1  server3.web-stat.com
127.0.0.1  server4.web-stat.com
127.0.0.1  www.web-stat.com
127.0.0.1  count.webtrackingservices.com
127.0.0.1  seomatrix.webtrackingservices.com
# [Green Horse Corporation][Adware.TickerBar]
127.0.0.1  greenhorse.com
127.0.0.1  www.greenhorse.com #[SunBelt.Greenhorse]
127.0.0.1  tickerbar.info
127.0.0.1  graphics.tickerbar.info
# [Gromozon.Rootkit]
127.0.0.1  alte6yacvjac.com
127.0.0.1  bsuzmfqidmi.com
127.0.0.1  bxbo9tgcgqu.com
127.0.0.1  callsolutions.biz #[Rootkit.DialCall]
127.0.0.1  e-46.com
127.0.0.1  et2lmgeeol.com
127.0.0.1  glgwzqmeqkt.com
127.0.0.1  guerdonde.com
127.0.0.1  ib2iql8q5lkb.com
127.0.0.1  ifiplqkg.com
127.0.0.1  www.itzzot.cc
127.0.0.1  kopythian.com
127.0.0.1  lqmubivaei.com
127.0.0.1  nzebisrizh.com
127.0.0.1  rac5kymzk6u.com
127.0.0.1  rolahujkzq.com
127.0.0.1  szig0z2rqud.com
127.0.0.1  szme9fqgwgg2.com
127.0.0.1  tordok.com
127.0.0.1  ubfajyin.com
127.0.0.1  ufvjeev4jrmk.com
127.0.0.1  uqbvru5am.com
127.0.0.1  vaozkn4yi.com
127.0.0.1  wbl2ishoweqf.com
127.0.0.1  xjgbm5sec6r.com
127.0.0.1  xjjhd6zk6.com
127.0.0.1  xuwdezt1.com
# [Hayter Merchants Group]
127.0.0.1  2youx.net
127.0.0.1  highdialer.com #[PcTools.Trojan.Downloader.Agent.SY]
127.0.0.1  www.highdialer.com
# [HispaNetwork Serv Informaticos]
127.0.0.1  ads.geoads.net
127.0.0.1  gs.geoads.net
127.0.0.1  hb.geoads.net
127.0.0.1  ib.geoads.net
127.0.0.1  images.geoads.net
127.0.0.1  overture.geoads.net
127.0.0.1  delivery.publicidad.net
# [HITEXCHANGE]
127.0.0.1  hitexchange.net
127.0.0.1  gif.hitexchange.net
127.0.0.1  img.hitexchange.net
127.0.0.1  www.hitexchange.net
127.0.0.1  hitx.net
127.0.0.1  gif.hitx.net
127.0.0.1  www.hitx.net
# [HK Internet Investments]
127.0.0.1  www1.consumeralertsystem.com #[McAfee.Adware-Fizzle]
127.0.0.1  www.consumeralertsystem.com #[PcTools.CasinoClient]
127.0.0.1  dailydealjunky.com
127.0.0.1  www.dailynewsjunky.com
# [HOMESTEAD]
127.0.0.1  stats.homestead.com
127.0.0.1  track.homestead.com
127.0.0.1  track2.homestead.com
# [Hosting Media]
127.0.0.1  homepage.main-hosting.com #[TROJ_STARTPAG.YC]
# [HOTBAR][Oren Dobronsky][Zango]
127.0.0.1  www.datez.com
127.0.0.1  emoticons4us.com
127.0.0.1  www.emoticons4us.com
127.0.0.1  www.estationery.com
127.0.0.1  www.ezaza.com
127.0.0.1  e-zaza.com
127.0.0.1  www.e-zaza.com
127.0.0.1  fastutilities.com
127.0.0.1  www.fastutilities.com
127.0.0.1  adopt.hbmediapro.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.hotbar-inc.com
127.0.0.1  hotbar.com #[SPYW_HOTBAR.P][AdWare.Win32.180Solutions.ay]
127.0.0.1  adopt.hotbar.com #[eTrust.Tracking.Cookie]
127.0.0.1  ads.hotbar.com #[SpySweeper.Spy.Cookie]
127.0.0.1  cs.hotbar.com
127.0.0.1  dynamic.hotbar.com
127.0.0.1  dynmenu.hotbar.com
127.0.0.1  hbmd.hotbar.com
127.0.0.1  installs.hotbar.com #[Win32/Adware.HotBar][McAfee.Adware-HotBar]
127.0.0.1  license.hotbar.com
127.0.0.1  partners.hotbar.com
127.0.0.1  promos.hotbar.com
127.0.0.1  puv.hotbar.com
127.0.0.1  reports.hotbar.com
127.0.0.1  searchdisp.hotbar.com
127.0.0.1  skins.hotbar.com
127.0.0.1  tooltips.hotbar.com
127.0.0.1  updates.hotbar.com
127.0.0.1  vip-farm1.hotbar.com
127.0.0.1  vip-farm2.hotbar.com
127.0.0.1  vip-farm1v.hotbar.com
127.0.0.1  vip-farm2v.hotbar.com
127.0.0.1  vip-farm5v.hotbar.com
127.0.0.1  vip-farm31v.hotbar.com
127.0.0.1  www.hotbar.com #[ADW_HOTBAR.O][Edelman.HotBar][Win32.Adware.HotBar]
127.0.0.1  www.hotbar2.com
127.0.0.1  www.hotbar.net
127.0.0.1  hotbarmemberdirectory.com
127.0.0.1  net-offers.net
127.0.0.1  www.pcpolish.com
127.0.0.1  priceshield.com
127.0.0.1  cfg.shopperreports.com
127.0.0.1  code.shopperreports.com
127.0.0.1  cs.shopperreports.com #[Trackware.SmartShopper]
127.0.0.1  dynamic.shopperreports.com
127.0.0.1  reports.shopperreports.com #[Adware-HotBar.dr]
127.0.0.1  updates.shopperreports.com
127.0.0.1  upgrades.shopperreports.com #[AdWare.Win32.Shopper.k]
127.0.0.1  www.shopperreports.com #[Adware-ShopprReports]
127.0.0.1  smartshopper.com #[IE-SpyAd]
127.0.0.1  cs.smartshopper.com #[McAfee.Adware-SmartShopper]
127.0.0.1  installs.smartshopper.com
127.0.0.1  www.smartshopper.com
127.0.0.1  www.smartshoppernetworks.com
127.0.0.1  software4thenet.com
127.0.0.1  www.software4thenet.com
127.0.0.1  spamblockerutility.com
127.0.0.1  installs.spamblockerutility.com
127.0.0.1  www.spamblockerutility.com #[SiteAdvisor.spamblockerutility.com]
127.0.0.1  www.spamfree.com
127.0.0.1  page-not-found.net #[McAfee.Adware-HotBar]
127.0.0.1  shopperreports.pricetool.com #[Hotbar.ShoppingReports]
127.0.0.1  resultsmaster.com
127.0.0.1  www.resultsmaster.com #[Adware.Hotbar]
127.0.0.1  wowpapers.com
127.0.0.1  www.wowpapers.com #[Win32.Adware.HotBar]
# [HOTLOG][eTrust Tracking.Cookie]
127.0.0.1  ad.hotlog.ru
127.0.0.1  click.hotlog.ru
127.0.0.1  globalstats.hotlog.ru
127.0.0.1  hit.hotlog.ru #[SecuritySpace.WebBug]
127.0.0.1  hit1.hotlog.ru
127.0.0.1  hit2.hotlog.ru
127.0.0.1  hit3.hotlog.ru
127.0.0.1  hit4.hotlog.ru
127.0.0.1  hit5.hotlog.ru
127.0.0.1  hit6.hotlog.ru
127.0.0.1  hit7.hotlog.ru
127.0.0.1  hit8.hotlog.ru #[SpySweeper.Spy.Cookie]
127.0.0.1  hit9.hotlog.ru
127.0.0.1  hit10.hotlog.ru
127.0.0.1  hit11.hotlog.ru
127.0.0.1  hit12.hotlog.ru
127.0.0.1  hit13.hotlog.ru #[SunBelt.HotLog.ru]
127.0.0.1  hit14.hotlog.ru
127.0.0.1  hit15.hotlog.ru
127.0.0.1  hit16.hotlog.ru
127.0.0.1  hit17.hotlog.ru
127.0.0.1  hit18.hotlog.ru
127.0.0.1  hit19.hotlog.ru
127.0.0.1  hit20.hotlog.ru
127.0.0.1  hit21.hotlog.ru
127.0.0.1  hit22.hotlog.ru
127.0.0.1  hit23.hotlog.ru
127.0.0.1  img.hotlog.ru
127.0.0.1  www1.hotlog.ru
127.0.0.1  www2.hotlog.ru #[Tenebril.Tracking.Cookie]
127.0.0.1  www3.hotlog.ru
127.0.0.1  www4.hotlog.ru
127.0.0.1  www5.hotlog.ru
127.0.0.1  www6.hotlog.ru #[Ewido.TrackingCookie.Hotlog]
127.0.0.1  www7.hotlog.ru
127.0.0.1  www8.hotlog.ru
127.0.0.1  www9.hotlog.ru
127.0.0.1  www10.hotlog.ru
127.0.0.1  www11.hotlog.ru
127.0.0.1  www12.hotlog.ru
127.0.0.1  www14.hotlog.ru
127.0.0.1  www.hotlog.ru
# [Hula Direct]
127.0.0.1  www.4netrevenue.com
127.0.0.1  hits.clickandtrack.net #[SpySweeper.Spy.Cookie]
127.0.0.1  www.huladirect.com
127.0.0.1  www.looking-younger.com
# [Hyperbanner Accordnet Ltd]
127.0.0.1  ads.bidvertiser.com
127.0.0.1  bdv.bidvertiser.com
127.0.0.1  www.bidvertiser.com #[SiteAdvisor.Bidvertiser]
127.0.0.1  ads05.bpath.com
127.0.0.1  ads06.bpath.com
127.0.0.1  ads07.bpath.com #[SunBelt.BPath.com]
127.0.0.1  ads08.bpath.com
127.0.0.1  ads09.bpath.com
127.0.0.1  ads10.bpath.com
127.0.0.1  ads12.bpath.com
127.0.0.1  ads13.bpath.com
127.0.0.1  ads14.bpath.com
127.0.0.1  ads15.bpath.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads16.bpath.com
127.0.0.1  ads17.bpath.com
127.0.0.1  ads18.bpath.com
127.0.0.1  ads19.bpath.com
127.0.0.1  ads20.bpath.com #[Tenebril.Tracking.Cookie]
127.0.0.1  ads21.bpath.com
127.0.0.1  ads22.bpath.com
127.0.0.1  ads23.bpath.com
127.0.0.1  ads24.bpath.com
127.0.0.1  ads25.bpath.com
127.0.0.1  ads26.bpath.com
127.0.0.1  ads27.bpath.com
127.0.0.1  ads28.bpath.com
127.0.0.1  ads49.bpath.com
127.0.0.1  australia.bpath.com
127.0.0.1  holland.bpath.com
127.0.0.1  spms.bpath.com
127.0.0.1  usa.bpath.com
127.0.0.1  www.bpath.com
# [Iclicks Internet Inc][617577 BC Ltd]
127.0.0.1  billingsupportcenter.com
127.0.0.1  www.billingsupportcenter.com
127.0.0.1  getclicksnow.com
127.0.0.1  www.getclicksnow.com
127.0.0.1  pur9.killevidence.com
127.0.0.1  www3.killevidence.com
127.0.0.1  www9.killevidence.com
127.0.0.1  www.killevidence.com
127.0.0.1  www3.killinternetpopups.com
127.0.0.1  www.killinternetpopups.com
127.0.0.1  mainstreamdollars.com
127.0.0.1  www2.mainstreamdollars.com
127.0.0.1  www.mainstreamdollars.com #[W32/HotSearchBar.D]
127.0.0.1  megapornbucks.com #[i-lookup.com]
127.0.0.1  mgallery.megapornbucks.com #[exits.freepornpics.com]
127.0.0.1  www9.megapornbucks.com
127.0.0.1  www.megapornbucks.com
# [iDownload][Click Feel Media]
127.0.0.1  032439.com
127.0.0.1  80gw6ry3i3x3qbrkwhxhw.032439.com #[Kephyr.PUP][Wildcard DNS]
127.0.0.1  1188224372.com
127.0.0.1  124365.com
127.0.0.1  202124388.com
127.0.0.1  79452436.com
127.0.0.1  82430.com
127.0.0.1  82435.com
127.0.0.1  z166o1s1kfkha8gsnfm9gq.82435.com #[SiteAdvisor.sexybabesx.com]
127.0.0.1  872435.com
127.0.0.1  924329928.com #[Command Desktop Advertising]
127.0.0.1  command.adservs.com #[c2.mii.instacontent.net][AdWare.Win32.MDH.e]
127.0.0.1  csx.adservs.com #[Norman.W32/Downloader]
127.0.0.1  csxiwwwcom.net
127.0.0.1  e8675309.com
127.0.0.1  ekads.com
127.0.0.1  equalitylinks.net
127.0.0.1  www.errordns.com
127.0.0.1  www.findstuffsearch.com
127.0.0.1  in.hushware.com
127.0.0.1  www.hushware.com
127.0.0.1  idbl.idblg.com
127.0.0.1  affiliate.idownload.com
127.0.0.1  beta.idownload.com
127.0.0.1  cftrack.idownload.com
127.0.0.1  md.idownload.com
127.0.0.1  secure.idownload.com
127.0.0.1  www.idownload.com #[Wildcard DNS]
127.0.0.1  in.interboost.com
127.0.0.1  www.interboost.com
127.0.0.1  auto.isearch.com #[Parasite.Pugi/iSearch][c2.mii.instacontent.net]
127.0.0.1  auto.origin.isearch.com
127.0.0.1  content.isearch.com #[c2.mii.instacontent.net]
127.0.0.1  dist.isearch.com #[Wildcard DNS]
127.0.0.1  toolbar.isearch.com #[MHTMLRedir.Exploit][Spyware.ISearch]
127.0.0.1  www.isearch.com #[ADW_ISEARCH.A][SPYW_DESKTOPS.11]
127.0.0.1  nutpond.com
127.0.0.1  www.popblocker.com
127.0.0.1  in.securefavorites.com
127.0.0.1  www.securefavorites.com
127.0.0.1  spywareavenger.com #[Rogue/Suspect]
127.0.0.1  in.spywareavenger.com
127.0.0.1  www.spywareavenger.com
127.0.0.1  tilde75.com
127.0.0.1  in.virushunter.com
127.0.0.1  www.virushunter.com #[Parked?]
127.0.0.1  in.wmkiller.com
127.0.0.1  www.wmkiller.com
# [iEntry Inc]
127.0.0.1  aj.600z.com
127.0.0.1  text-link-ads.ientry.com
127.0.0.1  action.ientry.net
127.0.0.1  aj.ientry.net
127.0.0.1  ca.ientry.net
127.0.0.1  img1.ientry.net
127.0.0.1  tracking.ientry.net
# [IE PLUGIN LIMITED][Adware.IEPlugin]
127.0.0.1  ieplugin.com
127.0.0.1  badurl.ieplugin.com
127.0.0.1  search.ieplugin.com #[IEPlugin.Search]
127.0.0.1  sysupdate.ieplugin.com #[Win32/TrojanDownloader.OneClickNetS.F]
127.0.0.1  welcome.ieplugin.com
127.0.0.1  wwa.ieplugin.com
127.0.0.1  wwd.ieplugin.com
127.0.0.1  ww2.ieplugin.com
127.0.0.1  ww3.ieplugin.com
127.0.0.1  www.ieplugin.com #[SiteAdvisor.ieplugin.com]
# [Ilissos][EyeBlaster][eTrust.BS.Serving-Sys]
127.0.0.1  ds.eyeblaster.com #[SunBelt.Eyeblaster][a158.x.akamai.net]
127.0.0.1  activity.serving-sys.com
127.0.0.1  bs.serving-sys.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  datacapture.serving-sys.com
127.0.0.1  ds.serving-sys.com #[Ewido.TrackingCookie.Serving-sys][a158.x.akamai.net]
127.0.0.1  ds-ll.serving-sys.com #[eyeblas.vo.llnwd.net]
# [ImagineNET]
127.0.0.1  www1.3dstats.com
127.0.0.1  www.3dstats.com
127.0.0.1  addfreestats.com #[SecuritySpace.WebBug]
127.0.0.1  top.addfreestats.com
127.0.0.1  www.addfreestats.com
127.0.0.1  www1.addfreestats.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www2.addfreestats.com
127.0.0.1  www3.addfreestats.com
127.0.0.1  www4.addfreestats.com #[eTrust.Tracking.Cookie]
127.0.0.1  www5.addfreestats.com
127.0.0.1  www6.addfreestats.com
127.0.0.1  www7.addfreestats.com
127.0.0.1  www8.addfreestats.com
# [Imperial e-club Limited]
127.0.0.1  banner.casinodelrio.com
127.0.0.1  banner.casinotropez.com #[Adware.Casino]
127.0.0.1  www.casinotropez.com #[Ewido.TrackingCookie.Casinotropez]
127.0.0.1  banner.europacasino.com
127.0.0.1  cachebanner.europacasino.com #[p.mii.instacontent.net]
127.0.0.1  cachewww.europacasino.com #[p.mii.instacontent.net]
127.0.0.1  banner.titanpoker.com #[Adware.Casino]
127.0.0.1  cachebanner.titanpoker.com #[p.mii.instacontent.net]
127.0.0.1  banner.vegasred.com #[Ewido.TrackingCookie.Vegasred]
127.0.0.1  cachebanner.vegasred.com #[p.mii.instacontent.net]
# [IMR Worldwide][Nielsen/NetRatings]
127.0.0.1  measurement.redsheriff.com
127.0.0.1  www.redsheriff.com
127.0.0.1  www.redsheriff.com.au
127.0.0.1  www.RedSheRRif.com
127.0.0.1  devfw.imrworldwide.com
127.0.0.1  lycos-eu.imrworldwide.com
127.0.0.1  ninemsn.imrworldwide.com
127.0.0.1  secure-asia.imrworldwide.com
127.0.0.1  secure-au.imrworldwide.com
127.0.0.1  secure-cn.imrworldwide.com #[NNR Site Census]
127.0.0.1  secure-dk.imrworldwide.com
127.0.0.1  secure-it.imrworldwide.com
127.0.0.1  secure-sg.imrworldwide.com #[SunBelt.IMRworldwide]
127.0.0.1  secure-jp.imrworldwide.com
127.0.0.1  secure-nz.imrworldwide.com
127.0.0.1  secure-uk.imrworldwide.com
127.0.0.1  secure-us.imrworldwide.com
127.0.0.1  secure-za.imrworldwide.com
127.0.0.1  server-au.imrworldwide.com
127.0.0.1  server-br.imrworldwide.com
127.0.0.1  server-by.imrworldwide.com
127.0.0.1  server-de.imrworldwide.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  server-dk.imrworldwide.com
127.0.0.1  server-ee.imrworldwide.com
127.0.0.1  server-fi.imrworldwide.com
127.0.0.1  server-it.imrworldwide.com
127.0.0.1  server-jp.imrworldwide.com
127.0.0.1  server-lv.imrworldwide.com
127.0.0.1  server-lt.imrworldwide.com
127.0.0.1  server-no.imrworldwide.com
127.0.0.1  server-nz.imrworldwide.com
127.0.0.1  server-oslo.imrworldwide.com
127.0.0.1  server-pl.imrworldwide.com
127.0.0.1  server-se.imrworldwide.com
127.0.0.1  server-sg.imrworldwide.com
127.0.0.1  server-stockh.imrworldwide.com
127.0.0.1  server-uk.imrworldwide.com
127.0.0.1  server-us.imrworldwide.com
127.0.0.1  survey1-au.imrworldwide.com
127.0.0.1  telstra.imrworldwide.com
127.0.0.1  www.imrworldwide.com #[McAfee.Cookie-Imrworldwide]
# [Inspower Networks]
127.0.0.1  www.blogfaces.com
127.0.0.1  www.blogpopunder.com #[server down?]
127.0.0.1  www.blogvisitors.com
127.0.0.1  www.link2blogs.com
127.0.0.1  www.theblogcompany.com
# [Internet REIT Inc][Netster][Parking Service]
127.0.0.1  park.ireit.com
127.0.0.1  park2.ireit.com
127.0.0.1  park3.ireit.com #[Microsoft.Typo-Patrol]
127.0.0.1  webdocs.ireit.com
127.0.0.1  advertise.netster.com #[SiteAdvisor.netster.com]
127.0.0.1  lb5.netster.com
127.0.0.1  pixel.netster.com #[Web bug]
127.0.0.1  lb1.youbettersearch.com
# [Inet-Traffic, Inc]
127.0.0.1  www.freehomepages.com
127.0.0.1  www.gameroom.com
127.0.0.1  www.inet-clix.com #[eTrust.Searchit][Wildcard DNS]
127.0.0.1  inet-traffic.com
127.0.0.1  ads.inet-traffic.com
127.0.0.1  banner1.inet-traffic.com
127.0.0.1  banner2.inet-traffic.com #[SpySweeper.Spy.Cookie]
127.0.0.1  banner3.inet-traffic.com
127.0.0.1  delivery.inet-traffic.com #[Parasite.Pugi][Adware.IntDel]
127.0.0.1  phplive.inet-traffic.com
127.0.0.1  www.inet-traffic.com
127.0.0.1  www.inetraffic.com #[server down?]
127.0.0.1  www.inettraffic.com
127.0.0.1  searchit.com #[Parasite.Pugi][McAfee.Adware-SearchIt]
127.0.0.1  news.searchit.com
127.0.0.1  toolbar.searchit.com #[SunBelt.SearchIt Toolbar]
127.0.0.1  www.searchit.com #[Spyware.IEToolbar]
127.0.0.1  www.tadpolls.com
# [Infinite Innovations][Parasite.BrowserAid][Adware.BrowserAid]
127.0.0.1  browseraid.com
127.0.0.1  pops.browseraid.com
127.0.0.1  st.browseraid.com #[WebDownloader]
127.0.0.1  updates.browseraid.com
127.0.0.1  uptodate.browseraid.com #[App/QuickL-A]
127.0.0.1  www.browseraid.com #[ADW_BROWSERAID.E]
127.0.0.1  www.quicklaunch.com
127.0.0.1  searchandclick.com
127.0.0.1  search.searchandclick.com
127.0.0.1  www.searchandclick.com #[Parasite.Browseraid][SearchAndClick]
127.0.0.1  startium.com
127.0.0.1  search.startium.com
127.0.0.1  www.startium.com
# [InsightExpress, LLC]
127.0.0.1  ad.insightexpress.com
127.0.0.1  invite.insightexpress.com
127.0.0.1  www.insightexpress.com #[Lavasoft.BannedSite]
127.0.0.1  ad.insightexpressai.com #[SiteAdvisor.insightexpressai.com]
127.0.0.1  ai003.insightexpressai.com #[TrendMicro.Internet Cookie]
127.0.0.1  ai004.insightexpressai.com
127.0.0.1  ai005.insightexpressai.com #[McAfee.Cookie-Insightexpres]
127.0.0.1  ai006.insightexpressai.com
127.0.0.1  ai007.insightexpressai.com
127.0.0.1  ai008.insightexpressai.com
127.0.0.1  ai009.insightexpressai.com
127.0.0.1  ai010.insightexpressai.com
127.0.0.1  ai011.insightexpressai.com
127.0.0.1  ai017.insightexpressai.com
127.0.0.1  ai020.insightexpressai.com
127.0.0.1  ai022.insightexpressai.com
127.0.0.1  ai026.insightexpressai.com
127.0.0.1  ai030.insightexpressai.com
127.0.0.1  ai031.insightexpressai.com
127.0.0.1  ai036.insightexpressai.com
127.0.0.1  ai048.insightexpressai.com
127.0.0.1  ai053.insightexpressai.com
127.0.0.1  ai056.insightexpressai.com
127.0.0.1  ai057.insightexpressai.com
127.0.0.1  ai059.insightexpressai.com
127.0.0.1  ai063.insightexpressai.com
127.0.0.1  ai066.insightexpressai.com
127.0.0.1  ai067.insightexpressai.com
127.0.0.1  ai076.insightexpressai.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ai078.insightexpressai.com #[SiteAdvisor.aim.com]
127.0.0.1  ai102.insightexpressai.com
127.0.0.1  ai131.insightexpressai.com
127.0.0.1  ai631.insightexpressai.com
127.0.0.1  ai637.insightexpressai.com
127.0.0.1  ai676.insightexpressai.com
127.0.0.1  ai694.insightexpressai.com
127.0.0.1  icompass.insightexpressai.com
127.0.0.1  core.insightexpressai.com
127.0.0.1  rb.insightexpressai.com
127.0.0.1  ai089.insightexpress.com
127.0.0.1  insightexpresserdd.com #[SiteAdvisor.galttech.com]
# [Interpolls]
127.0.0.1  hs.interpolls.com #[a1765.g.akamai.net]
127.0.0.1  nbc.interpolls.com
127.0.0.1  pollserver.interpolls.com
127.0.0.1  ps2.interpolls.com
127.0.0.1  ps.interpolls.com
127.0.0.1  sw.interpolls.com
127.0.0.1  wb.interpolls.com
# [Interep Interactive]
127.0.0.1  chewbacca.cybereps.com
127.0.0.1  ds.cybereps.com
127.0.0.1  images.cybereps.com
127.0.0.1  oascentral.cybereps.com #[RealMedia]
127.0.0.1  www.cybereps.com #[SunBelt.Cybereps.com]
127.0.0.1  yoda.cybereps.com
# [Internext Media Corp]
127.0.0.1  abcsearch.com
127.0.0.1  admin.abcsearch.com
127.0.0.1  www3.abcsearch.com #[Browseraid]
127.0.0.1  www.abcsearch.com
127.0.0.1  abosearch.com
127.0.0.1  www.abosearch.com
127.0.0.1  cashclicks.com
127.0.0.1  www.cashclicks.com
127.0.0.1  www.primosearch.com
127.0.0.1  www1.searchwho.com
127.0.0.1  www.searchwho.com
# [IPower Pro]
127.0.0.1  ads.iboost.com
# [i-Serve Promotions]
127.0.0.1  pluto.adcycle.com #[Whios.Blacklisted]
127.0.0.1  www.adcycle.com
127.0.0.1  www.exchange-it.com
127.0.0.1  media.exchange-it.com
127.0.0.1  metacount.com
127.0.0.1  stats.metacount.com
127.0.0.1  www.metacount.com
127.0.0.1  popunder.com
127.0.0.1  media.popunder.com
127.0.0.1  www.popunder.com
# [Jayde Online]
127.0.0.1  exactseek.com #[Adware.Win32.ExactSeek]
127.0.0.1  ads.exactseek.com
127.0.0.1  www.exactseek.com #[Win32/Adware.SearchIt][MVPS.Criteria]
# [Jeremy Buzik]
127.0.0.1  ppc.burnsearch.net
127.0.0.1  www.burnsearch.net
127.0.0.1  www.cleandrive2007.com #[Symantec.PCCleaner]
127.0.0.1  kicksearch.net
127.0.0.1  lookall.net
127.0.0.1  driveclean.lookme.biz
127.0.0.1  www.lookme.biz #[VBS/TrojanDownloader.Psyme.Gen]
127.0.0.1  www.xxx-upload.net
# [Joint Stock Company]
127.0.0.1  ad.bannerbank.ru
127.0.0.1  ad1.bannerbank.ru
127.0.0.1  ad2.bannerbank.ru
127.0.0.1  ad3.bannerbank.ru
127.0.0.1  ad4.bannerbank.ru
127.0.0.1  ad5.bannerbank.ru
127.0.0.1  ad6.bannerbank.ru #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ad7.bannerbank.ru
127.0.0.1  ad8.bannerbank.ru
127.0.0.1  ad9.bannerbank.ru
127.0.0.1  ad10.bannerbank.ru
127.0.0.1  ad11.bannerbank.ru
127.0.0.1  ad12.bannerbank.ru
127.0.0.1  crd1.bannerbank.ru
127.0.0.1  ad.ir.ru
# [Jorgen Koefoed]
127.0.0.1  download3.payoutpal.com #[TROJ_ZEROLIN.A]
127.0.0.1  download4.payoutpal.com #[Adware.Cax][CAX Object]
127.0.0.1  resellerstats.payoutpal.com
127.0.0.1  www.payoutpal.com
# [JSC Dewis Group]
127.0.0.1  cracks4u.com #[Win32/TrojanDownloader.Adload.DS]
127.0.0.1  getcracks.com #[Win32/TrojanDownloader.Adload.DS]
127.0.0.1  keygen.name #[Trojan-Dropper.Win32.Pakes]
127.0.0.1  www.seriall.com #[Trojan-Dropper.Win32.Pakes]
127.0.0.1  www.thekeys.ws #[Google Warning]
# [Kabanga Corp][Kontera Technologies]
127.0.0.1  chat.ezula.com
127.0.0.1  app.ezula.com
127.0.0.1  www.ezula.com #[eTrust.Ezula]
127.0.0.1  kabanga.com
127.0.0.1  www.kabanga.com
127.0.0.1  dc.kontera.com
127.0.0.1  kona.kontera.com #[DynamiContext AdLinks][MVPS.Criteria]
127.0.0.1  kona2.kontera.com
127.0.0.1  kona3.kontera.com
127.0.0.1  kona4.kontera.com
127.0.0.1  kona5.kontera.com
127.0.0.1  te.kontera.com
127.0.0.1  te100.kontera.com
127.0.0.1  www.kontera.com
# [KIM HYUNGHO]
127.0.0.1  goi.com
127.0.0.1  nav.goi.com
127.0.0.1  nav.hitq.com
127.0.0.1  hitq.com
# [Klikdomains Group]
127.0.0.1  online-topsearch-adult.info
127.0.0.1  www.online-topsearch-adult.info
# [Legendum LLC][Tracking Service]
127.0.0.1  db0.net-filter.com #[WebtraffIQ Code]
127.0.0.1  db2.net-filter.com
127.0.0.1  db3.net-filter.com
127.0.0.1  db4.net-filter.com
127.0.0.1  db5.net-filter.com
127.0.0.1  db6.net-filter.com
127.0.0.1  db7.net-filter.com
127.0.0.1  sitestats.com #[Ewido.TrackingCookie.Sitestat]
127.0.0.1  db0.sitestats.com
127.0.0.1  db1.sitestats.com
127.0.0.1  db2.sitestats.com
127.0.0.1  db3.sitestats.com
127.0.0.1  db4.sitestats.com
127.0.0.1  db5.sitestats.com
127.0.0.1  db6.sitestats.com
127.0.0.1  db7.sitestats.com
127.0.0.1  www.sitestats.com
# [Lightningcast]
127.0.0.1  stream11.instream.com
127.0.0.1  stats.lightningcast.net
127.0.0.1  stats2.lightningcast.net
# [Lincoln Sales][MYVOD,Inc]
127.0.0.1  download.targetnetworks.net
127.0.0.1  www.targetnetworks.net #[Adware-SmartPops.dldr]
# [LinkShare]
127.0.0.1  ad.linksynergy.com #[SpySweeper.Spy.Cookie]
127.0.0.1  click.linksynergy.com #[eTrust.Tracking.Cookie]
127.0.0.1  m.banner.linksynergy.com #[Tenebril.Tracking.Cookie]
127.0.0.1  ssl.linksynergy.com #[SecuritySpace.WebBug]
127.0.0.1  www.linkshare.com
# [LIST.RU]
127.0.0.1  ad1.lbe.ru
127.0.0.1  list.ru
127.0.0.1  host1.list.ru
127.0.0.1  host3.list.ru
127.0.0.1  host4.list.ru
127.0.0.1  host7.list.ru
127.0.0.1  host11.list.ru
127.0.0.1  host12.list.ru
127.0.0.1  host13.list.ru
127.0.0.1  host14.list.ru
127.0.0.1  top.list.ru
127.0.0.1  top1.list.ru
# [little help software]
127.0.0.1  www.little-help.com
127.0.0.1  little-download.net #[Adware.Littlehelper]
127.0.0.1  www.little-download.net
127.0.0.1  games.de.ag
127.0.0.1  www.de.ag #[McAfee.Adware-Littlehelper]
# [LivePerson]
127.0.0.1  hc2.humanclick.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.humanclick.com #[McAfee.Cookie-Humanclick]
127.0.0.1  www.liveperson.com
127.0.0.1  liveperson.net #[SecuritySpace.WebBug][McAfee.Cookie-Liveperson]
127.0.0.1  sales.liveperson.net #[Tenebril.Tracking.Cookie]
127.0.0.1  sec1.liveperson.net #[SpySweeper.Spy.Cookie]
127.0.0.1  server.iad.liveperson.net #[Spyware:Cookie/Server.iad.Liveperson]
# [LiveTechnology International]
127.0.0.1  14713804a.l2m.net #[SpySweeper.Spy.Cookie]
127.0.0.1  jmm.livestat.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.livestat.com #[SunBelt.Livestat.com]
127.0.0.1  www.livetechnology.com
# [Longview Media][ExitFuel]
127.0.0.1  404errorpage.com
127.0.0.1  www.404errorpage.com
127.0.0.1  bigclicks.com
127.0.0.1  search.bigclicks.com
127.0.0.1  www.bigclicks.com
127.0.0.1  link.exitdirect.com
127.0.0.1  www.exitdirect.com
127.0.0.1  gohip.com #[McAfee.Gohip Freevideo]
127.0.0.1  dev.gohip.com
127.0.0.1  foundry.gohip.com
127.0.0.1  previewstage.gohip.com
127.0.0.1  search.gohip.com
127.0.0.1  stage.gohip.com
127.0.0.1  stats.gohip.com
127.0.0.1  wmservera.gohip.com
127.0.0.1  www.gohip.com #[eTrust.Browser Enhancement]
127.0.0.1  www.homelandnetwork.com #[SunBelt.Homeland Network][Parked?]
127.0.0.1  staging.netbroadcaster.com
127.0.0.1  www6.netbroadcaster.com #[IE-SpyAd]
127.0.0.1  www.netbroadcaster.com #[HJTH.NetBroadCaster/MovieNetworks]
127.0.0.1  searchfuel.com
127.0.0.1  search.searchfuel.com
127.0.0.1  wwwdev.searchfuel.com
127.0.0.1  weirdontheweb.net #[SunBelt.Cok.weirdontheweb]
127.0.0.1  oascentral.weirdontheweb.net #[RealMedia]
127.0.0.1  staging.weirdontheweb.net
127.0.0.1  www.weirdontheweb.net #[Adware.WeirdOnTheWeb][Adware-SmartPops.dldr]
127.0.0.1  search.winnings.com
# [Longview Media via AccessMedia Software][Digital Enterprises]
127.0.0.1  download.accessmedia.tv
127.0.0.1  images.accessmedia.tv
127.0.0.1  members.accessmedia.tv
127.0.0.1  secure.accessmedia.tv
127.0.0.1  staging.accessmedia.tv
127.0.0.1  toolbar.accessmedia.tv
127.0.0.1  www.accessmedia.tv
127.0.0.1  notifier.altbill.com
127.0.0.1  notifier.altpayments.com #[McAfee.Adware-Fuel]
127.0.0.1  www.broadcaster.com
127.0.0.1  www.mediacaster.net #[Adware.MovieLand/MediaPipe]
127.0.0.1  download.movieland.com
127.0.0.1  members.movieland.com
127.0.0.1  track.movieland.com
127.0.0.1  www.movieland.com #[Fortinet.Adware/Fuel][McAfee.Adware-Fuel]
127.0.0.1  images.moviepass.tv
127.0.0.1  members.moviepass.tv
127.0.0.1  staging.download.mediapipe.tv
127.0.0.1  www.moviepass.tv #[Trojan.Muvipaz]
127.0.0.1  popcorn.net
127.0.0.1  download.popcorn.net
127.0.0.1  members.popcorn.net
127.0.0.1  track.popcorn.net
127.0.0.1  www.sexbroadcaster.com
127.0.0.1  ads.vitalix.net #[images.accessmedia.tv][Trojan.Muvipaz]
127.0.0.1  www.voddirect.com
127.0.0.1  ads.webmastersdirect.com
# [Longview Media via Dawn of Time][Click2Media][Search Networks]
127.0.0.1  search.123-search.net #[search-exe.com]
127.0.0.1  search.media-search.net
127.0.0.1  www.media-search.net
127.0.0.1  search.scourweb.net
127.0.0.1  search.search-assist.net
127.0.0.1  search.sidebarsearch.com
# [Lycos, Inc]
127.0.0.1  ads2.jubii.dk #[ads-dk.spray.net]
127.0.0.1  fe.lea.jubii.dk #[ads-dk.spray.net]
127.0.0.1  ads.lycos.com
127.0.0.1  cm8.lycos.com
127.0.0.1  guestworld.tripod.lycos.com
127.0.0.1  client.sidesearch.lycos.com #[Parasite.SideSearch]
127.0.0.1  install.sidesearch.lycos.com #[ADW_SIDESEARCH.A][Adware.SideSearch]
127.0.0.1  titan.guestworld.tripod.lycos.com
127.0.0.1  ads.lycos-europe.com
127.0.0.1  fe.lea.lycos.de
127.0.0.1  ads.multimania.lycos.fr
127.0.0.1  ads.tripod.lycos.de
127.0.0.1  ads.tripod.lycos.es
127.0.0.1  ads.tripod.lycos.co.uk
127.0.0.1  ads.tripod.lycos.nl #[Ad-Aware.Tracking.Cookie]
127.0.0.1  oreo.matchmaker.com
127.0.0.1  fe.lea.spray.se
127.0.0.1  ads.tripod.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads1.tripod.com #[SunBelt.Tripod]
127.0.0.1  nedstat.tripod.com
# [m3 Media Services]
127.0.0.1  awrz.net
127.0.0.1  d.m3.net
127.0.0.1  d.ak.m3.net
127.0.0.1  i.m3.net
# [Mamma Media Solutions]
127.0.0.1  focusin.com
127.0.0.1  www-401.focusin.com
127.0.0.1  www.focusin.com
127.0.0.1  ads.mamma.com #[SunBelt.Mamma]
127.0.0.1  ad2.mamma.com
127.0.0.1  targetnet.com #[McAfee.Cookie-Targetnet]
127.0.0.1  fad-401.mtl4.targetnet.com
127.0.0.1  fad-403.mtl4.targetnet.com
127.0.0.1  fad-404.mtl4.targetnet.com
127.0.0.1  fad-406.mtl4.targetnet.com
127.0.0.1  fad-408.mtl4.targetnet.com
127.0.0.1  fad-409.mtl4.targetnet.com #[FavoriteMan Class][HJTH.SpyAssult]
127.0.0.1  fad-411.mtl4.targetnet.com #[FavoriteMan Class]
127.0.0.1  fad-412.mtl4.targetnet.com
127.0.0.1  fad-413.mtl4.targetnet.com
127.0.0.1  fad-1103.nyc1.targetnet.com #[FavoriteMan Class]
127.0.0.1  fad-1104.nyc1.targetnet.com
127.0.0.1  fad-1105.nyc1.targetnet.com
127.0.0.1  fad-1106.nyc1.targetnet.com
127.0.0.1  fad-1107.nyc1.targetnet.com
127.0.0.1  fad-1108.nyc1.targetnet.com #[FavoriteMan Class]
127.0.0.1  fad-1109.nyc1.targetnet.com #[HJTH.SpyAssult]
127.0.0.1  fad-1110.nyc1.targetnet.com
127.0.0.1  fad-1111.nyc1.targetnet.com
127.0.0.1  fad-1112.nyc1.targetnet.com
127.0.0.1  fad-1113.nyc1.targetnet.com
127.0.0.1  fad-1114.nyc1.targetnet.com
127.0.0.1  fad-1115.nyc1.targetnet.com
127.0.0.1  focusin.ads.targetnet.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.targetnet.com #[SunBelt.Targetnet.com]
# [Marchex, Inc][MDNH, Inc][TrafficLeader][UltSearch]
127.0.0.1  ads.ah-ha.com
127.0.0.1  ads2.ah-ha.com
127.0.0.1  cp.ah-ha.com
127.0.0.1  partner.ah-ha.com #[Troj/Subsear-A][Adware-SSF.dr]
127.0.0.1  secure.ah-ha.com
127.0.0.1  drivelinemedia.com
127.0.0.1  ads.drivelinemedia.com
127.0.0.1  ads2.drivelinemedia.com
127.0.0.1  images.drivelinemedia.com
127.0.0.1  www.drivelinemedia.com
127.0.0.1  c.enhance.com #[Panda.Spyware:Cookie/Enhance]
127.0.0.1  images.enhance.com #[McAfee.Cookie-Enhance]
127.0.0.1  www.enhance.com
127.0.0.1  goclick.com
127.0.0.1  c.goclick.com #[SpySweeper.Spy.Cookie]
127.0.0.1  earth.goclick.com
127.0.0.1  partner1.goclick.com
127.0.0.1  venus.goclick.com
127.0.0.1  www.goclick.com #[McAfee.Cookie-Goclick]
127.0.0.1  gflinks.industrybrains.com
127.0.0.1  ilinks.industrybrains.com
127.0.0.1  imglinks.industrybrains.com
127.0.0.1  jlinks.industrybrains.com #[Whois.Blacklisted]
127.0.0.1  shlinks.industrybrains.com
127.0.0.1  mdnhinc.com
127.0.0.1  c.mdnhinc.com
127.0.0.1  cb.mdnhinc.com
127.0.0.1  cb.openclick.com
127.0.0.1  ads.trafficleader.com
127.0.0.1  images.ultsearch.com
127.0.0.1  imagesb.ultsearch.com
127.0.0.1  www.ultsearch.com
# [Market Engines Group]
127.0.0.1  adwarepro.com #[Rogue/Suspect]
127.0.0.1  www.adwarepro.com
127.0.0.1  avforce.com #[SiteAdvisor.avforce.com]
127.0.0.1  cashengines.com #[SiteAdvisor.cashengines.com]
127.0.0.1  click.cashengines.com
127.0.0.1  www.cashengines.com
127.0.0.1  defenza.com
127.0.0.1  www.defenza.com
127.0.0.1  drmengines.com
127.0.0.1  www.dvdsoftwarereview.info
127.0.0.1  fixwinmx.com
127.0.0.1  imusicaccess.com #[SiteAdvisor.imusicaccess.com]
127.0.0.1  helpdesk.marketbill.com
127.0.0.1  www.marketbill.com
127.0.0.1  download2.marketengines.com
127.0.0.1  secure.marketengines.com
127.0.0.1  secure3.marketengines.com
127.0.0.1  www.mp3downloading.com
127.0.0.1  www.netspyprotector.com #[Rogue/Suspect]
127.0.0.1  www.powercompress.com
127.0.0.1  richwebmedia.com
127.0.0.1  scripts.richwebmedia.com
127.0.0.1  www.richwebmedia.com
127.0.0.1  www.ultimatemoviedownload.com #[SiteAdvisor.ultimatemoviedownload.com]
# [Massive Incorporated][Game Ad Server]
127.0.0.1  madserver.net
127.0.0.1  ad.madserver.net
127.0.0.1  imp.madserver.net
127.0.0.1  media.madserver.net
# [MaxSearch Group][YAWSA LLC]
127.0.0.1  www.adoptim.com
127.0.0.1  ariboo.com #[goto.maxifiles.com]
127.0.0.1  de.ariboo.com
127.0.0.1  dk.ariboo.com
127.0.0.1  es.ariboo.com
127.0.0.1  fi.ariboo.com
127.0.0.1  fr.ariboo.com
127.0.0.1  nl.ariboo.com
127.0.0.1  uk.ariboo.com
127.0.0.1  www.ariboo.fr
127.0.0.1  www.ariboo.com
127.0.0.1  www.centralspeed.com #[ABI Network][speedtest.dll]
127.0.0.1  freeprod.com #[SunBelt.Freeprod/Toolbar888]
127.0.0.1  media.freeprod.com #[Adware/Toolbar888]
127.0.0.1  www.freeprod.com
127.0.0.1  www.fresh-weather.com #[Adware.Fresh]
127.0.0.1  greatmemo.com
127.0.0.1  jouezgagnant.com
127.0.0.1  activex.matcash.com
127.0.0.1  admin.matcash.com #[SpySweeper.Trojan.matcash]
127.0.0.1  connect.matcash.com
127.0.0.1  dynmedia.matcash.com
127.0.0.1  media.matcash.com #[TROJ_DLOADER.ZS][Win32/Anyhomb.D]
127.0.0.1  www.matcash.com
127.0.0.1  maxifiles.com
127.0.0.1  goto.maxifiles.com #[TROJ_DLOADER.ACA][Adware.Director]
127.0.0.1  network.maxifiles.com
127.0.0.1  xml.maxifiles.com
127.0.0.1  www.maxifiles.com #[Adware.MaxSearch][TR/Drop.Agent.aac]
127.0.0.1  www.maximpic.com #[speedtest.dll]
127.0.0.1  axcab.wrs.mcboo.com
127.0.0.1  dl.mcboo.com #[Win32/TrojanDownloader.PurityScan.NAH]
127.0.0.1  dr.mcboo.com #[Downloader-BCF]
127.0.0.1  dr26.mcboo.com
127.0.0.1  dr27.mcboo.com #[Wildcard DNS]
127.0.0.1  dr38.mcboo.com
127.0.0.1  dr43.mcboo.com
127.0.0.1  dr45.mcboo.com
127.0.0.1  j10.wrs.mcboo.com #[server down?]
127.0.0.1  wr.mcboo.com
127.0.0.1  maxcab.wrs.mcboo.com
127.0.0.1  wrs.mcboo.com
127.0.0.1  referenco.com
127.0.0.1  www.speedmeter.info #[speedtest.dll]
127.0.0.1  admin.teddycash.com
127.0.0.1  www.teddycash.com
127.0.0.1  admin.waverevenue.com
127.0.0.1  media.waverevenue.com
127.0.0.1  static.waverevenue.com
# [MC Squared][Kestral Communications]
127.0.0.1  www.fceboard.com #[Adware.EBoard]
127.0.0.1  www.iboard.com
127.0.0.1  www.kestralcom.com
127.0.0.1  www.mcsqd.com
# [Mediacolumn Marketing][Net Nucleus Corp]
127.0.0.1  ny.contentmatch.net #[Trojan.TrustedZones]
127.0.0.1  download.getmirar.com #[Adware.Mirar]
127.0.0.1  www.getmirar.com #[SPYW_GETMIRAR.A]
127.0.0.1  mirarsearch.com
127.0.0.1  click.mirarsearch.com #[Trojan.TrustedZones]
127.0.0.1  redirect.mirarsearch.com #[Trojan.TrustedZones]
127.0.0.1  static.mirarsearch.com
127.0.0.1  www.mirarsearch.com
127.0.0.1  awbeta.net-nucleus.com #[SunBelt.net-nucleus]
127.0.0.1  www.net-nucleus.com #[McAfee.Adware-Mirar]
# [Media Holding Enterprises]
127.0.0.1  data.context-tool.com
127.0.0.1  www.errors-tool.com
127.0.0.1  app.goodcleanonlinefun.com #[Malicious.Content.Zango]
127.0.0.1  playmp3z.biz
127.0.0.1  www.playmp3z.biz
# [Mermaid Consulting via Gerald Simpson]
127.0.0.1  deskwizz.com #[SunBelt.Deskwizz]
127.0.0.1  ads.deskwizz.com
127.0.0.1  apps.deskwizz.com #[TROJ_ENVOLO.B][DR/Dldr.Small.ctp]
127.0.0.1  media.deskwizz.com
127.0.0.1  www.deskwizz.com
# [Mermaid Consulting via Micro Point][Robert Lapierre][S. S. Marketing]
127.0.0.1  www.allthatsearch.com
127.0.0.1  www.finditlive.com
127.0.0.1  www.jumptothat.com
127.0.0.1  www.link-hunter.com
127.0.0.1  www.my-stats.com
127.0.0.1  banners.searchingbooth.com #[Ewido.TrackingCookie.Searchingbooth]
127.0.0.1  www.searchingbooth.com #[Win32/Zquest.A]
127.0.0.1  www.seek-zone.com
127.0.0.1  top-banners.com #[SunBelt.KGhost]
127.0.0.1  media.top-banners.com #[TROJ_ENVOLO.B][Whois.Blacklisted]
127.0.0.1  www.top-banners.com #[Adware.QuickBrowser][Win32/Actux.A]
# [Messenger Service Spammer via Branch Software]
127.0.0.1  secure.branchsoftware.com
127.0.0.1  www.registrycleanerexpress.com
127.0.0.1  www.registrycleanergold.com
127.0.0.1  www.registrycleanerxp.com
# [Michael Richardson]
127.0.0.1  www.blockmessengerspam.com
127.0.0.1  www.blockthesepopups.com
127.0.0.1  www.endmessenger.com
127.0.0.1  www.fightpopups.net #[Adware.MessStopper]
127.0.0.1  www.messengersoft.com
# [MicroSmarts Enterprise][TrojanClicker.Win32.Swind.a]
127.0.0.1  www.freespywarescan.org #[SiteAdvisor.freespywarescan.org]
127.0.0.1  www.magicphotoshow.com
127.0.0.1  www.popupbegone.com
127.0.0.1  searchgateway.net #[Parasite.SearchGateway]
127.0.0.1  www.searchgateway.net
127.0.0.1  www.secure-processingcenter.com
127.0.0.1  showbehind.com #[Adware.ShowBehind]
127.0.0.1  www.showbehind.com #[ADW_SWIND.A]
127.0.0.1  www.spywarebegone.com
127.0.0.1  spywarevanisher.com
127.0.0.1  www.spywarevanisher.com
127.0.0.1  worldusa.com #[Trojan.Win32.StartPage.oz]
127.0.0.1  www.worldusa.com #[Trojan.StartPage-CD]
127.0.0.1  www.zipitfast.com
# [Microsoft Corporation]
127.0.0.1  ad2.adecn.com
127.0.0.1  ad5.adecn.com #[SpySweeper.Spy.Cookie]
127.0.0.1  cds.adecn.com #[p.mii.instacontent.net]
127.0.0.1  fastcounter.bcentral.com #[SecuritySpace.WebBug]
127.0.0.1  fcstats.bcentral.com
# [Microsoft MSN Ad Servers]
127.0.0.1  msnads-wm9.fplive.net #[MSN Video Ads]
127.0.0.1  ads.msn.com
127.0.0.1  ads1.msn.com
127.0.0.1  a.ads1.msn.com #[global.msads.net.c.footprint.net]
127.0.0.1  b.ads1.msn.com
127.0.0.1  ads.eu.msn.com
127.0.0.1  ads.ninemsn.com.au
127.0.0.1  arc2.msn.com
127.0.0.1  arc3.msn.com
127.0.0.1  arc9.msn.com
127.0.0.1  popup.msn.com
# 127.0.0.1  rad.msn.com #[affects MSN Messenger]
127.0.0.1  a.rad.msn.com #[ADSAdClient31.dll]
127.0.0.1  b.rad.msn.com
127.0.0.1  rmads.msn.com
127.0.0.1  rmads.eu.msn.com
127.0.0.1  a.global.msads.net
127.0.0.1  global.msads.net
# [MindViz]
127.0.0.1  ads.mindviz.com #[SiteAdvisor.mindviz.com]
127.0.0.1  traffic.mindviz.com
127.0.0.1  mylinkbox.com
127.0.0.1  box.mylinkbox.com
127.0.0.1  mvtracker.com #[MindViz Tracking Code]
127.0.0.1  ft.mvtracker.com
127.0.0.1  www.mvtracker.com
# [Mirror Image Internet][Tracking Service]
127.0.0.1  c.mii.instacontent.net
127.0.0.1  cserver.mii.instacontent.net
127.0.0.1  p.mii.instacontent.net
127.0.0.1  pd.mii.instacontent.net
127.0.0.1  pdownload.mii.instacontent.net
127.0.0.1  pserver.mii.instacontent.net
127.0.0.1  secure.instacontent.net
# [The MarketDart Corporation]
127.0.0.1  jraun.com #[WinEssential][Adware.Jraun]
127.0.0.1  www.jraun.com #[KeyActivex Control][SunBelt.Jraun]
127.0.0.1  karmajunction.com
127.0.0.1  www.karmamedia.com
127.0.0.1  marketdart.com #[Spyware.Marketdart]
127.0.0.1  www.marketdart.com
# [Mark Hostetler]
127.0.0.1  find-fm.com #[AdWare.Win32.Softomate.e]
127.0.0.1  adult.find.fm #[eTrust.Softomate.FindFM]
127.0.0.1  www.find.fm #[AdWare.SideSearch.g]
127.0.0.1  peakclick.com #[SiteAdvisor.peakclick.com]
127.0.0.1  feed.peakclick.com
127.0.0.1  www.peakclick.com #[AdWare.SideSearch.g][FindFmToolbar]
127.0.0.1  www.pharmacywebsearch.com #[Spamdexing]
127.0.0.1  results-today.com
127.0.0.1  veryfastsearch.com
127.0.0.1  www.veryfastsearch.com
# [Marketscore Inc][Relevant Knowledge][ComScore]
127.0.0.1  www.e-trends.com #[Proxy-OSS]
127.0.0.1  marketscore.com #[Spyware.Marketscore]
127.0.0.1  optout.marketscore.com #[mailingsvcs.com]
127.0.0.1  oss-ad.marketscore.com #[SiteAdvisor.kiwialpha.com]
127.0.0.1  oss-adtest.marketscore.com
127.0.0.1  oss-content.marketscore.com #[Ewido.Spyware.MarketScore]
127.0.0.1  oss-content.gta.marketscore.com #[SunBelt.MarketScore.com]
127.0.0.1  oss-crules.marketscore.com #[Panda.Spyware/MarketScore]
127.0.0.1  oss-survey.marketscore.com
127.0.0.1  proxycfg.marketscore.com #[Server-Proxy.Win32.MarketScore.k]
127.0.0.1  www.marketscore.com #[eTrust.MarketScore]
127.0.0.1  www.permissionresearch.com
127.0.0.1  relevantknowledge.com
127.0.0.1  www.relevantknowledge.com #[SunBelt.Marketscore.RelevantKnowledge]
127.0.0.1  rules.securestudies.com
127.0.0.1  www.surveyscore.com #[server down?]
127.0.0.1  www.surveysite.com
127.0.0.1  web.survey-poll.com
127.0.0.1  www2.survey-poll.com
# [Michael Levin]
127.0.0.1  815.hittail.com
127.0.0.1  922.hittail.com
127.0.0.1  1262.hittail.com
127.0.0.1  3415.hittail.com
127.0.0.1  3463.hittail.com
127.0.0.1  3918.hittail.com
127.0.0.1  3957.hittail.com
127.0.0.1  4134.hittail.com
127.0.0.1  4560.hittail.com
127.0.0.1  4612.hittail.com
127.0.0.1  8260.hittail.com
127.0.0.1  8959.hittail.com
127.0.0.1  9394.hittail.com
127.0.0.1  9446.hittail.com
127.0.0.1  9547.hittail.com
127.0.0.1  9563.hittail.com
127.0.0.1  9571.hittail.com
127.0.0.1  10006.hittail.com
127.0.0.1  10168.hittail.com
127.0.0.1  12877.hittail.com
127.0.0.1  13223.hittail.com
127.0.0.1  14228.hittail.com
127.0.0.1  15141.hittail.com
127.0.0.1  16565.hittail.com
127.0.0.1  19500.hittail.com
127.0.0.1  117.mylongtail.com
127.0.0.1  317.mylongtail.com
127.0.0.1  327.mylongtail.com
127.0.0.1  505.mylongtail.com
127.0.0.1  582.mylongtail.com
# [MinuteGroup Ltd][Barak Avitbul]
127.0.0.1  dv-networks.com #[server down?]
127.0.0.1  www.mailcleaner.com #[McAfee.Adware-VCatch]
127.0.0.1  www.minutegroup.com
# [Miva Corporation][FindWhat.com, Inc][Starware]
127.0.0.1  cache.bandofbuddies.com #[p.mii.instacontent.net]
127.0.0.1  www.bandofbuddies.com
127.0.0.1  bandofbuddys.com
127.0.0.1  www.cursorcafe.com
127.0.0.1  admedia.xmlsearch.findwhat.com #[SpySweeper.Spy.Cookie]
127.0.0.1  netster.xmlsearch.findwhat.com #[SunBelt.Findwhat]
127.0.0.1  us01.xmlsearch.findwhat.com
127.0.0.1  adrevenue.findwhat.com
127.0.0.1  analytics.findwhat.com #[Ad Analyzer Code]
127.0.0.1  getfound.com #[Parasite.GogoTools]
127.0.0.1  search.getfound.com
127.0.0.1  www.getfound.com #[Troj/Getfound-A]
127.0.0.1  arx.us.miva.com #[MIVA AdRevenue][SiteAdvisor.reka-traffa.com]
127.0.0.1  cb.us.miva.com
127.0.0.1  search.uk.miva.com
127.0.0.1  v10.xmlsearch.miva.com #[McAfee.Adware-Zeno]
127.0.0.1  cache.screensavers.com
127.0.0.1  cachef.screensavers.com #[p.mii.instacontent.net]
127.0.0.1  dm.screensavers.com #[Win32/Adware.Comet][AdWare.Win32.Comet.ac]
127.0.0.1  f.screensavers.com #[Fortinet.Adware/Cometsys]
127.0.0.1  i.screensavers.com #[SpySweeper.Spy.Cookie][hitbox.com]
127.0.0.1  www.screensavers.com #[AdWare.Win32.Comet.bd]
127.0.0.1  www.searchfeed.com
127.0.0.1  files.searchrover.net
127.0.0.1  www.smileytown.com
127.0.0.1  as.starware.com #[Adware.Starware]
127.0.0.1  cachetry.starware.com #[p.mii.instacontent.net]
127.0.0.1  files-pl.starware.com #[Adware.Starware.F]
127.0.0.1  h.starware.com #[SpySweeper.Adware.starware]
127.0.0.1  my.starware.com
127.0.0.1  search.starware.com #[McAfee.Adware-Starware]
127.0.0.1  sl.starware.com #[AdWare.Win32.Comet.aq]
127.0.0.1  try.starware.com #[SunBelt.Starware.Toolbar]
127.0.0.1  www.starware.com #[McAfee.Adware-StartToolBar]
127.0.0.1  as.weatherstudio.com #[McAfee.WStudio]
127.0.0.1  files.weatherstudio.com
127.0.0.1  my.weatherstudio.com
127.0.0.1  try.weatherstudio.com #[try.starware.com]
127.0.0.1  www.weatherstudio.com
# [MKI Inc]
127.0.0.1  esearchme.info #[Trackware.SearchTerms]
127.0.0.1  esearchmaster.info
127.0.0.1  searchaccess.info
# [myGeek.com][Visicom Media]
127.0.0.1  adonlist.com
127.0.0.1  adonlistings.com
127.0.0.1  www.adondirect.com
127.0.0.1  context.adontext.com
127.0.0.1  context2.adontext.com
127.0.0.1  testing.adontext.com
127.0.0.1  www.adonnetwork.com
127.0.0.1  ad.cpvfeed.com #[SiteAdvisor.cpvfeed.com]
127.0.0.1  campaign.cpvfeed.com
127.0.0.1  conversion.cpvfeed.com
127.0.0.1  cpvtext.cpvfeed.com
127.0.0.1  keyword.cpvfeed.com
127.0.0.1  roitrack.cpvfeed.com #[Ewido.TrackingCookie.Cpvfeed]
127.0.0.1  url.cpvfeed.com
127.0.0.1  www.expandsearch.com #[Adware.Expand]
127.0.0.1  toolbar.gograph.com
127.0.0.1  mbkwbar.com
127.0.0.1  ads.mbkwbar.com
127.0.0.1  config.mbkwbar.com #[Adware.MBKWbar]
127.0.0.1  report.mbkwbar.com #[Ewido.Spyware.BetterInternet]
127.0.0.1  www.mbkwbar.com
127.0.0.1  amazing.mygeek.com #[SunBelt.MyGeek.com]
127.0.0.1  categories.mygeek.com #[SiteAdvisor.mygeek.com]
127.0.0.1  offeroptimizer.mygeek.com
127.0.0.1  partners.mygeek.com #[SearchCentrix]
127.0.0.1  searchhippo.mygeek.com
127.0.0.1  tp.mygeek.com
127.0.0.1  xmlsearch.mygeek.com
127.0.0.1  www.mygeekdirect.com
127.0.0.1  www.mygeeksearch.com
127.0.0.1  searchcentrix.com #[Adware.SideBar][Adware.SearchCentrix]
127.0.0.1  downloads.searchcentrix.com #[SomaticCAB.Setup]
127.0.0.1  if.searchcentrix.com #[StartPage-GN]
127.0.0.1  internetfuel.searchcentrix.com
127.0.0.1  www.searchcentrix.com #[VisiCom.SearchCentric]
127.0.0.1  vmn.net
127.0.0.1  seek4freetoolbar.mygeek.com
127.0.0.1  www.x2revenue.com #[server down?]
127.0.0.1  www.x2revenuesearch.com
# [Name Administration Inc]
127.0.0.1  2o7.com
127.0.0.1  www.2o7.com
127.0.0.1  images.15x.net #[IE-SpyAd]
127.0.0.1  track.15x.net
127.0.0.1  wdc.15x.net
127.0.0.1  ws1.15x.net
127.0.0.1  ws2.15x.net
127.0.0.1  ws3.15x.net
127.0.0.1  www.downloadboost.com #[eTrust.Win32/Beovens]
127.0.0.1  linkz.com #[Adware.AdBlock]
127.0.0.1  adblock.linkz.com #[AdBlock APInstaller Class]
127.0.0.1  www2.linkz.com
127.0.0.1  www.linkz.com
127.0.0.1  litas.com #[Trojan.backdoor.win32.agent.KY]
127.0.0.1  munky.com
127.0.0.1  www.munky.com
127.0.0.1  nameadmininc.com
127.0.0.1  www.nameadmininc.com
127.0.0.1  www.nameadministration.com
127.0.0.1  namedia.com
127.0.0.1  www.pagina.com
127.0.0.1  pimpout.com
127.0.0.1  www.pimpout.com
127.0.0.1  www.searchmagnifier.com
127.0.0.1  virtumondo.com
# [NetIQ Corporation][Tracking Service]
127.0.0.1  ctix8.cheaptickets.com #[cheaptickets.webtrends.akadns.net]
127.0.0.1  wt.ticketmaster.com #[ticketmaster.webtrends.akadns.net]
127.0.0.1  m.webtrends.com #[microsoft.webtrends.akadns.net]
127.0.0.1  webtrendslive.com #[SmartSource Data Collector]
127.0.0.1  statse.webtrendslive.com #[SDC Advanced Tracking Code]
127.0.0.1  dcs.wtlive.com #[SpySweeper.Spy.Cookie]
127.0.0.1  dcstest.wtlive.com
127.0.0.1  www.webtrends.net #[SunBelt.WebTrends]
127.0.0.1  www.netiq.com
# [NetIQ via Misc Sites]
127.0.0.1  wtrs.101com.com
127.0.0.1  dcs.mattel.com
127.0.0.1  sdc.goapply.com
127.0.0.1  sdc.bettycrocker.com
127.0.0.1  sdc.boxtops4education.com
127.0.0.1  sdc.brightcove.com
127.0.0.1  sdc.ca.com
127.0.0.1  sdc.dtag.com
127.0.0.1  sdc.entertainment.com
127.0.0.1  sdc.grandsphere.net
127.0.0.1  sdc.hfmus.com
127.0.0.1  sdc.hln.be
127.0.0.1  ssdc.icelandair.com
127.0.0.1  ssdc.icelandair.is
127.0.0.1  ssdc.icelandair.net
127.0.0.1  sdc.kaboose.com
127.0.0.1  sdc.mcafee.com #[statse.webtrendslive.com]
127.0.0.1  sdc.plannedparenthood.org
127.0.0.1  sdc.radio-canada.ca
127.0.0.1  sdc.rbistats.com
127.0.0.1  sdc.traderonline.com
127.0.0.1  sdc.valpak.com
127.0.0.1  sdc.tvguide.com
127.0.0.1  sdc.windowsmarketplace.com
127.0.0.1  wdcs.trendmicro.com
# [Netsaits BV]
127.0.0.1  cz2.clickzs.com #[SpySweeper.Spy.Cookie]
127.0.0.1  cz3.clickzs.com
127.0.0.1  cz4.clickzs.com #[Malicious.Links.Codec]
127.0.0.1  cz5.clickzs.com
127.0.0.1  cz6.clickzs.com
127.0.0.1  cz7.clickzs.com #[Ewido.TrackingCookie.Clickzs]
127.0.0.1  cz8.clickzs.com
127.0.0.1  cz9.clickzs.com
127.0.0.1  cz11.clickzs.com
127.0.0.1  js.clickzs.com
127.0.0.1  js3.clickzs.com #[Tenebril.Tracking.Cookie]
127.0.0.1  js4.clickzs.com
127.0.0.1  js5.clickzs.com
127.0.0.1  js6.clickzs.com
127.0.0.1  js7.clickzs.com
127.0.0.1  js8.clickzs.com
127.0.0.1  js9.clickzs.com
127.0.0.1  js11.clickzs.com
127.0.0.1  jsp.clickzs.com
127.0.0.1  jsp2.clickzs.com
127.0.0.1  vip.clickzs.com
127.0.0.1  vip2.clickzs.com
127.0.0.1  www.clickzs.com #[SunBelt.Clickzs.com]
127.0.0.1  www.dialer-dollars.com
127.0.0.1  www.hit-now.com
127.0.0.1  gthumbs.netsaits.com
# [Nedstat BV][Webstats4U][Tracking Service]
127.0.0.1  www.nedstat.com
127.0.0.1  nedstat.net #[SunBelt.Nedstat]
127.0.0.1  be.nedstat.net
127.0.0.1  es.nedstat.net
127.0.0.1  de.sitestat.nedstat.net
127.0.0.1  uk.nedstat.net
127.0.0.1  usa.nedstat.net
127.0.0.1  nedstat.nl
127.0.0.1  nedstat.s0.nl
127.0.0.1  www.nedstat.nl
127.0.0.1  nedstatbasic.net #[SecuritySpace.WebBug]
127.0.0.1  m1.nedstatbasic.net
127.0.0.1  nl.nedstatbasic.net
127.0.0.1  usa.nedstatbasic.net
127.0.0.1  v1.nedstatbasic.net
127.0.0.1  www.nedstatbasic.net
127.0.0.1  m1.nedstatpro.net
127.0.0.1  nl.nedstatpro.net
127.0.0.1  uk.nedstatpro.net
127.0.0.1  www.nedstat.co.uk
127.0.0.1  sitestat.com
127.0.0.1  be.sitestat.com
127.0.0.1  de.sitestat.com
127.0.0.1  es.sitestat.com
127.0.0.1  fr.sitestat.com
127.0.0.1  int.sitestat.com #[SiteAdvisor.azter.com]
127.0.0.1  nl.sitestat.com
127.0.0.1  uk.sitestat.com
127.0.0.1  nbasic.sitestat.net
127.0.0.1  www.sitestat.com
127.0.0.1  m1.webstats4u.com
127.0.0.1  www.webstats4u.com
# [Network Solutions]
127.0.0.1  ads.netsol.com
127.0.0.1  ads.networksolutions.com
127.0.0.1  code.superstats.com
127.0.0.1  stats.superstats.com #[SunBelt.SuperStats]
# [MISC NEWS SITES][Tracking Service]
127.0.0.1  adireland.com
127.0.0.1  www3.adireland.com
127.0.0.1  www.adireland.com
127.0.0.1  www.adquest3d.com #[WebTrends]
127.0.0.1  aa.oasfile.aftenposten.no
127.0.0.1  ad.aftenposten.no #[RealMedia]
127.0.0.1  adcache.aftenposten.no
127.0.0.1  webhit.aftenposten.no
127.0.0.1  ad.aftonbladet.se #[RealMedia]
127.0.0.1  ads.allafrica.com
127.0.0.1  ads.anm.co.uk #[SpySweeper.Spy.Cookie]
127.0.0.1  ads.apn.co.nz #[McAfee.Cookie-Apn]
127.0.0.1  ads.mm.ap.org
127.0.0.1  adnet.asahi.com
127.0.0.1  ads.bangkokpost.co.th
127.0.0.1  stats.bbc.co.uk
127.0.0.1  ads.bcnewsgroup.com
127.0.0.1  ads.bloomberg.com
127.0.0.1  ads.bninews.com
127.0.0.1  rmedia.boston.com
127.0.0.1  ads.businessweek.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads5.canoe.ca
127.0.0.1  ads.cantonrep.com
127.0.0.1  ads.casinocity.com
127.0.0.1  as1.casinocity.com
127.0.0.1  adimg1.chosun.com
127.0.0.1  cad.chosun.com #[RealMedia]
127.0.0.1  hitlog2.chosun.com
127.0.0.1  dart.chron.com #[DART AdSpace]
127.0.0.1  adtrack.cimedia.net
127.0.0.1  realaudio.cimedia.net
127.0.0.1  ads.clubplanet.com
127.0.0.1  ads.comicbookresources.com
127.0.0.1  ads3.condenast.co.uk
127.0.0.1  ads.cosmosmagazine.com
127.0.0.1  webtrendssdc.covers.com
127.0.0.1  ads.thecrimson.com
127.0.0.1  ads.digitalhealthcare.com
127.0.0.1  delivery3.digitalhealthcare.com #[RealMedia]
127.0.0.1  ads.digitalmedianet.com
127.0.0.1  adserver.digitalmedianet.com
127.0.0.1  adverts.digitalspy.co.uk
127.0.0.1  www.dnps.com #[RealMedia]
127.0.0.1  banner.dwalliance.com
127.0.0.1  ads.eagleinteractive.com
127.0.0.1  iklan.emedia.com.my #[AdRevolver]
127.0.0.1  ads.emeraldcoast.com
127.0.0.1  ads.emol.com #[RealMedia]
127.0.0.1  adserver.ens-news.com
127.0.0.1  adverts.f-1.com
127.0.0.1  campaigns.f2.com.au
127.0.0.1  ads.fairfax.com.au
127.0.0.1  images.ads.fairfax.com.au
127.0.0.1  redirect.fairfax.com.au
127.0.0.1  ad1.firehousezone.com
127.0.0.1  ad2.firehousezone.com #[RealMedia]
127.0.0.1  ads.forbes.com #[RealMedia]
127.0.0.1  klipmart.forbes.com
127.0.0.1  ads.fredericksburg.com
127.0.0.1  onset.freedom.com
127.0.0.1  ads.ft.com
127.0.0.1  secureads.ft.com
127.0.0.1  ads.globalsportsmedia.com
127.0.0.1  gtrackz.com
127.0.0.1  adimage.guardian.co.uk
127.0.0.1  ads.guardian.co.uk
127.0.0.1  dclk.haaretz.com
127.0.0.1  dclk.haaretz.co.il
127.0.0.1  ad.hankooki.com
127.0.0.1  log.hankooki.com
127.0.0.1  adserver1.harvestadsdepot.com
127.0.0.1  oas.heise.de #[RealMedia]
127.0.0.1  ads.hellomagazine.com #[RealMedia]
127.0.0.1  id.hellomagazine.com #[Web bug]
127.0.0.1  ads.heraldsun.com #[RealMedia]
127.0.0.1  ads1.hometownannapolis.com
127.0.0.1  adserver.ifmagazine.com
127.0.0.1  advertising.illinimedia.com
127.0.0.1  www.indiads.com #[RealMedia]
127.0.0.1  ads.indiatimes.com #[McAfee.Cookie-Indiads]
127.0.0.1  adstil.indiatimes.com #[RealMedia]
127.0.0.1  insightxe.inq7.net
127.0.0.1  adsrv.iol.co.za
127.0.0.1  ad.itbe.com
127.0.0.1  adserver1.journalregister.com
127.0.0.1  ads.jpost.com #[RealMedia]
127.0.0.1  track.jpost.com #[server down?]
127.0.0.1  banners.kfmb.com
127.0.0.1  ads.ljworld.com
127.0.0.1  ads2.ljworld.com
127.0.0.1  v7.stats.load.com
127.0.0.1  ads.keloland.com
127.0.0.1  ad1.logger.co.kr
127.0.0.1  trk14.logger.co.kr
127.0.0.1  stats.macworld.com
127.0.0.1  ads.madison.com
127.0.0.1  g3t4d5.madison.com
127.0.0.1  oas.mainetoday.com #[RealMedia]
127.0.0.1  utils.media-general.com #[RealMedia]
127.0.0.1  ads.mgnetwork.com #[RealMedia]
127.0.0.1  te.mgnetwork.com #[McAfee.Cookie-Mgnetwork]
127.0.0.1  mas.midkotasolutions.com
127.0.0.1  www.midkotatraffic.net
127.0.0.1  admin.minyanville.com
127.0.0.1  ads1.moneycontrol.com
127.0.0.1  adserver.monstersandcritics.com
127.0.0.1  ads.morningstar.com #[RealMedia]
127.0.0.1  ad.moscowtimes.ru
127.0.0.1  adwatcher.mostvaluablenetwork.com
127.0.0.1  ads.movieweb.com
127.0.0.1  adserv.mywebtimes.com
127.0.0.1  adserver.newdigitalgroup.com #[RealMedia]
127.0.0.1  adserver.news.com.au #[SunBelt.AdServer.News.com]
127.0.0.1  adserver2.news-journalonline.com
127.0.0.1  ads.newsquest.co.uk #[RealMedia]
127.0.0.1  adsadmin.newsquest.co.uk #[RealMedia]
127.0.0.1  ads-delivery1.newsquest.co.uk #[RealMedia]
127.0.0.1  collector.newsx.cc
127.0.0.1  ads.northjersey.com #[RealMedia]
127.0.0.1  www2.northjersey.com
127.0.0.1  adserver.nydailynews.com #[RealMedia]
127.0.0.1  ads.nypost.com
127.0.0.1  oasis.nysun.com
127.0.0.1  ads.nytimes.com
127.0.0.1  rm.ocregister.com #[RealMedia]
127.0.0.1  adcount.ohmynews.com
127.0.0.1  ads.ozonemedia.co.in #[ozone.adbureau.net]
127.0.0.1  ads.pittsburghlive.com #[RealMedia]
127.0.0.1  webtrends.randallpub.com
127.0.0.1  rotabanner.rian.ru
127.0.0.1  collector.richmond.com #[DeepMetrix StatScript]
127.0.0.1  oas.roanoke.com
127.0.0.1  ads.ruralpress.com
127.0.0.1  maxads.ruralpress.com
127.0.0.1  ads.sabah.com.tr
127.0.0.1  ads.schwabtrader.com
127.0.0.1  ads.sddt.com
127.0.0.1  ads.sfomedia.com
127.0.0.1  pubad.shanghaidaily.com
127.0.0.1  ads.sify.com #[RealMedia]
127.0.0.1  oas.signonsandiego.com #[RealMedia]
127.0.0.1  ads.solutionsic.com
127.0.0.1  ads.soush.com
127.0.0.1  ads.space.com #[RealMedia]
127.0.0.1  ads.spootle.com
127.0.0.1  ads.sportingnews.com #[RealMedia]
127.0.0.1  ads.stabroeknews.com
127.0.0.1  ads.stephensmedia.com
127.0.0.1  adzone.stltoday.com
127.0.0.1  applets.sulekha.com #[ICICI Text Ads]
127.0.0.1  suads.sulekha.com
127.0.0.1  te.suntimes.com #[WebBug]
127.0.0.1  banners.sys-con.com
127.0.0.1  ads.swiftnews.com
127.0.0.1  dcs.swiftnews.com #[WebBug]
127.0.0.1  ads.technologyguide.com
127.0.0.1  ads.telegraph.co.uk #[McAfee.Cookie-Telegraph]
127.0.0.1  test.theeagle.com
127.0.0.1  ad.thehill.com
127.0.0.1  ads.thestar.com
127.0.0.1  te.thestar.com
127.0.0.1  mercury.tiser.com.au
127.0.0.1  adsys.townnews.com
127.0.0.1  ads.trackentertainment.com
127.0.0.1  adsrv1.velonews.com
127.0.0.1  adserver.virgin.net #[Ad-Aware Tracking.Cookie]
127.0.0.1  ads.wnd.com
127.0.0.1  jack.zap2it.com #[RealMedia]
127.0.0.1  ads.cluster01.oasis.zmh.zope.net
# [Misc News via Advance Publications Group]
127.0.0.1  ads.advance.net #[McAfee.Cookie-Advance]
127.0.0.1  ads1.advance.net #[RealMedia][eTrust.Tracking.Cookie]
127.0.0.1  ads.udc.advance.net
127.0.0.1  ads1.udc.advance.net
127.0.0.1  ads2.udc.advance.net
127.0.0.1  ads3.udc.advance.net
127.0.0.1  ads4.udc.advance.net
127.0.0.1  ads5.udc.advance.net
127.0.0.1  ads6.udc.advance.net
127.0.0.1  ads7.udc.advance.net
127.0.0.1  ads8.udc.advance.net
127.0.0.1  ads9.udc.advance.net
127.0.0.1  ads10.udc.advance.net
127.0.0.1  ads11.udc.advance.net
127.0.0.1  ads12.udc.advance.net
127.0.0.1  ads13.udc.advance.net
127.0.0.1  ads14.udc.advance.net
127.0.0.1  ads15.udc.advance.net
127.0.0.1  ads16.udc.advance.net
127.0.0.1  te.advance.net
127.0.0.1  ads.al.com #[ads.udc.advance.net]
127.0.0.1  ads.cleveland.com #[ads.udc.advance.net]
127.0.0.1  ads.golfdigest.com #[ads.udc.advance.net]
127.0.0.1  ads.masslive.com #[ads.udc.advance.net]
127.0.0.1  ads.mlive.com
127.0.0.1  ads.nj.com #[RealMedia][ads.udc.advance.net]
127.0.0.1  ads.nola.com #[RealMedia][ads.udc.advance.net]
127.0.0.1  ads.oregonlive.com #[ads.udc.advance.net]
127.0.0.1  ads.pennlive.com #[RealMedia][ads.udc.advance.net]
127.0.0.1  ads.silive.com
# [Misc News via American Media]
127.0.0.1  ads1.ami-admin.com
127.0.0.1  ads.fitpregnancy.com
127.0.0.1  ads.flexonline.com
127.0.0.1  ads.muscleandfitness.com
127.0.0.1  ads.muscleandfitnesshers.com
127.0.0.1  ads.nationalenquirer.com
127.0.0.1  ads.starmagazine.com #[ads.ami-admin.com]
# [Misc News via Belo Interactive]
127.0.0.1  te.azfamily.com
127.0.0.1  ads.belointeractive.com #[RealMedia][eTrust.Tracking.Cookie]
127.0.0.1  mysa.belointeractive.com
127.0.0.1  te.belointeractive.com
127.0.0.1  te.dallasnews.com
127.0.0.1  te.fox11az.com
127.0.0.1  te.king5.com
127.0.0.1  te.kgw.com
127.0.0.1  te.khou.com
127.0.0.1  te.krem.com
127.0.0.1  te.ktvb.com
127.0.0.1  te.kvue.com
127.0.0.1  te.mysanantonio.com
127.0.0.1  te.pe.com
127.0.0.1  te.quickdfw.com
127.0.0.1  te.wcnc.com
# [Misc News via Clear Channel]
127.0.0.1  ads4.clearchannel.com
127.0.0.1  w10.centralmediaserver.com
127.0.0.1  w11.centralmediaserver.com
# [Misc News via Gannett Media Technologies][USA Today]
127.0.0.1  gcirm.argusleader.gcion.com
127.0.0.1  q.azcentral.com
127.0.0.1  gcirm.battlecreekenquirer.gcion.com
127.0.0.1  gcirm.baxterbulletin.gcion.com
127.0.0.1  gcirm.burlingtonfreepress.gcion.com
127.0.0.1  gcirm.californianonline.gcion.com
127.0.0.1  gcirm.centralohio.gcion.com
127.0.0.1  gcirm.c-n.gcion.com
127.0.0.1  gcirm.cincinnati.gcion.com
127.0.0.1  gcirm.citizen-times.gcion.com
127.0.0.1  gcirm.clarionledger.gcion.com
127.0.0.1  gcirm.coloradoan.gcion.com
127.0.0.1  gcirm.courier-journal.com
127.0.0.1  gcirm.courierpostonline.gcion.com
127.0.0.1  gcirm.dailyrecord.gcion.com
127.0.0.1  gcirm.delawareonline.gcion.com
127.0.0.1  gcirm.delmarvanow.gcion.com
127.0.0.1  gcirm.democratandchronicle.com
127.0.0.1  gcirm.dmp.gcion.com
127.0.0.1  gcirm.dmregister.gcion.com
127.0.0.1  gcirm.dnj.gcion.com
127.0.0.1  gcirm.elpasotimes.com
127.0.0.1  gcirm.flatoday.gcion.com
127.0.0.1  gcirm.gannettnetwork.com
127.0.0.1  gcirm.gannett-tv.com
127.0.0.1  gcirm.gannettvideo.com
127.0.0.1  gcirm.greenvilleonline.gcion.com
127.0.0.1  gcirm.greatfallstribune.gcion.com
127.0.0.1  gcirm.guampdn.gcion.com
127.0.0.1  gcirm.hattiesburgamerican.gcion.com
127.0.0.1  gcirm.herald-dispatch.com
127.0.0.1  gcirm.honoluluadvertiser.gcion.com
127.0.0.1  gcirm.indystar.gcion.com
127.0.0.1  gcirm.injersey.gcion.com
127.0.0.1  gcirm.jacksonsun.gcion.com
127.0.0.1  gcirm.jconline.gcion.com
127.0.0.1  gcirm.laregionalonline.com
127.0.0.1  gcirm.laregionalonline.gcion.com
127.0.0.1  gcirm.lsj.gcion.com
127.0.0.1  gcirm.montgomeryadvertiser.gcion.com
127.0.0.1  gcirm.mydesert.gcion.com
127.0.0.1  gcirm.newsleader.gcion.com
127.0.0.1  gcirm.news-press.com
127.0.0.1  gcirm.norwichbulletin.com
127.0.0.1  gcirm.nyjournalnews.com
127.0.0.1  gcirm.ozarksnow.gcion.com
127.0.0.1  gcirm.pal-item.gcion.com
127.0.0.1  gcirm.pensacolanewsjournal.gcion.com
127.0.0.1  pathcontrol-att.pni.com
127.0.0.1  pathcontrol-xo.pni.com
127.0.0.1  q.pni.com
127.0.0.1  gcirm.poughkeepsiejournal.gcion.com
127.0.0.1  gcirm.rgj.gcion.com
127.0.0.1  gcirm.press-citizen.gcion.com
127.0.0.1  gcirm.pressconnects.gcion.com
127.0.0.1  gcirm.sctimes.com
127.0.0.1  gcirm.stargazette.gcion.com
127.0.0.1  gcirm.statesmanjournal.gcion.com
127.0.0.1  gcirm.tallahassee.gcion.com
127.0.0.1  gcirm.tennessean.gcion.com
127.0.0.1  gcirm.thedailyjournal.gcion.com
127.0.0.1  gcirm.thejournalnews.gcion.com
127.0.0.1  gcirm.theleafchronicle.gcion.com #[RealMedia]
127.0.0.1  gcirm.theithacajournal.gcion.com
127.0.0.1  gcirm.thespectrum.gcion.com
127.0.0.1  gcirm.thestarpress.gcion.com
127.0.0.1  gcirm.thetimesherald.gcion.com
127.0.0.1  gcirm.tucson.com
127.0.0.1  gcirm.usaweekend.com
127.0.0.1  gcirm.uticaod.com
127.0.0.1  gcirm.visaliatimesdelta.gcion.com
127.0.0.1  gcirm.wisinfo.com
127.0.0.1  ads5.mconetwork.com
127.0.0.1  ad.usatoday.com
127.0.0.1  ads.usatoday.com
127.0.0.1  c.usatoday.com
# [Misc News via McClatchy Interactive][Gannett Media]
127.0.0.1  ads.adn.com #[RealMedia]
127.0.0.1  ads.bakersfield.com
127.0.0.1  oas.bellinghamherald.com
127.0.0.1  ads.fresnobee.com #[oasads0.nandomedia.com]
127.0.0.1  ads.heraldonline.com
127.0.0.1  oas.idahostatesman.com
127.0.0.1  adsadmin.nandomedia.com
127.0.0.1  ads.newsobserver.com
127.0.0.1  ads.realcities.com
127.0.0.1  krd.realcities.com
127.0.0.1  ads.sacbee.com
127.0.0.1  oas.startribune.com
127.0.0.1  oas.theolympian.com
# [Misc News via Tacoda Systems]
127.0.0.1  te.about.com #[te.gslb.tacoda.net]
127.0.0.1  te.ap.org #[te.gslb.tacoda.net]
127.0.0.1  te.astrology.com #[ivillage.te.tacoda.net]
127.0.0.1  tste.astrology.com #[ivillage.tste.tacoda.net]
127.0.0.1  tste.azcentral.com #[McAfee.Cookie-Azcentral]
127.0.0.1  te.boston.com #[te.gslb.tacoda.net]
127.0.0.1  te.businessweek.com
127.0.0.1  te.cleveland.com #[Tacoda Code]
127.0.0.1  te.chron.com
127.0.0.1  tste.gay.com
127.0.0.1  tste.hamptonroads.com
127.0.0.1  te.infoworld.com #[te.gslb.tacoda.net]
127.0.0.1  tste.insidebayarea.com #[te.gslb.tacoda.net]
127.0.0.1  te.ivillage.com #[ivillage.te.tacoda.net]
127.0.0.1  tste.ivillage.com #[ivillage.tste.tacoda.net]
127.0.0.1  te.nytdigital.com #[te.gslb.tacoda.net]
127.0.0.1  te.nytimes.com #[te.gslb.tacoda.net]
127.0.0.1  tste.planetoutinc.com
127.0.0.1  tste.pno.net
127.0.0.1  te.signonsandiego.com #[te.gslb.tacoda.net]
127.0.0.1  te.sfgate.com #[te.gslb.tacoda.net][MVPS.Criteria]
127.0.0.1  tste.yorkdispatch.com #[te.gslb.tacoda.net]
# [Misc News via Tribune Company]
127.0.0.1  te.chicagotribune.com #[te.tribune.com]
127.0.0.1  te.courant.com
127.0.0.1  te.ctnow.com
127.0.0.1  te.dailypress.com
127.0.0.1  te.greenwichtime.com
127.0.0.1  te.latimes.com
127.0.0.1  te.mcall.com
127.0.0.1  te.newsday.com
127.0.0.1  te.orlandosentinel.com
127.0.0.1  te.sunspot.net
127.0.0.1  te.stamfordadvocate.com
127.0.0.1  te.sun-sentinel.com #[Tacoda Code]
127.0.0.1  te.trb.com
# [Misc News via Village Voice Media]
127.0.0.1  adindex.laweekly.com
127.0.0.1  adindex.nashvillescene.com
127.0.0.1  ads2.newtimes.com
127.0.0.1  adindex.ocweekly.com
127.0.0.1  adindex.seattleweekly.com
127.0.0.1  adindex.villagevoice.com
127.0.0.1  oas.villagevoice.com
# [New Media Properties]
127.0.0.1  www.allyoursearch.com #[TrojanDropper.Win32.Small.gt]
127.0.0.1  searchsquire.com #[Parasite.SearchSquire]
127.0.0.1  ad.searchsquire.com
127.0.0.1  search.searchsquire.com #[Trojan.TrustedZones]
127.0.0.1  update.searchsquire.com #[SunBelt.SearchSquire]
127.0.0.1  www.searchsquire.com #[Adware.Searchsquire]
# [netBridge Limited Cyprus]
127.0.0.1  a.boom.ro
127.0.0.1  ads.boom.ro
127.0.0.1  s.boom.ro
127.0.0.1  ads.softure.com
127.0.0.1  adserver.softure.com
127.0.0.1  stat1.trafic.ro
127.0.0.1  www.trafic.ro
# [NETVALUE SA][Spyware.Netrat]
127.0.0.1  de.opistat.com
127.0.0.1  download.opistat.com
127.0.0.1  premeter.opistat.com #[PcTools.NetRatings Premeter]
127.0.0.1  server.opistat.com
127.0.0.1  srv-fr.opistat.com
127.0.0.1  uk.opistat.com
127.0.0.1  uk2.opistat.com
127.0.0.1  www.opistat.com
# [Oemtec, Ltd][Rogue/Suspect][Adware-IEDriver]
127.0.0.1  rn11.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c.rn11.com #[a773.g.akamai.net]
127.0.0.1  i.rn11.com #[HJTH.InternetWasherPro ActiveX][pserver.mii.instacontent.net]
127.0.0.1  img.rn11.com
127.0.0.1  e.spamextract.com #[img.rn11.com.edgesuite.net]
127.0.0.1  spyspotter.com #[Symantec.spyspotter.com]
127.0.0.1  c.spyspotter.com #[a1393.g.akamai.net]
127.0.0.1  config.spyspotter.com
127.0.0.1  download.spyspotter.com #[a1487.g.akamai.net]
127.0.0.1  e.spyspotter.com
127.0.0.1  www.spyspotter.com #[SunBelt.SpySpotter]
127.0.0.1  download.oemji.com
127.0.0.1  search.oemji.com #[a1139.g.akamai.net]
127.0.0.1  www.oemji.com #[eTrust.Oemji Bar][Adware.Oemji]
# [Omniture][Wildcard DNS]
127.0.0.1  2o7.net #[McAfee.Cookie-2O7][Ewido.TrackingCookie.2o7]
127.0.0.1  102.112.207.net #[2 zero 7]
127.0.0.1  102.112.2o7.net #[Tenebril.Tracking.Cookie]
127.0.0.1  102.122.2o7.net #[Panda.Spyware:Cookie/2o7.net]
127.0.0.1  192.168.112.2o7.net #[SpySweeper.Spy.Cookie]
127.0.0.1  3gupload.112.2o7.net
127.0.0.1  acckalaharinet.112.2o7.net
127.0.0.1  adbrite.122.2o7.net
127.0.0.1  advertisingcom.122.2o7.net
127.0.0.1  aehistory.112.2o7.net
127.0.0.1  aetv.112.2o7.net
127.0.0.1  affilcrtopcolle.112.2o7.net
127.0.0.1  agamgreetingscom.112.2o7.net
127.0.0.1  agbmcom.112.2O7.net
127.0.0.1  agegreetings.112.2o7.net
127.0.0.1  agmsnag.112.2o7.net
127.0.0.1  ameritradeogilvy.112.2o7.net
127.0.0.1  ameritradeamerivest.112.2o7.net
127.0.0.1  angiba.112.2o7.net
127.0.0.1  angmar.112.2o7.net
127.0.0.1  angmil.112.2o7.net
127.0.0.1  angpar.112.2O7.net
127.0.0.1  aolbks.122.2o7.net
127.0.0.1  aolcamember.122.2o7.net
127.0.0.1  aolcg.122.2o7.net
127.0.0.1  aolcmp.122.2o7.net
127.0.0.1  aolcommem.122.2o7.net
127.0.0.1  aolcsmen.122.2o7.net
127.0.0.1  aoldlama.122.2o7.net
127.0.0.1  aoldrambuie.122.2o7.net
127.0.0.1  aolgam.122.2o7.net
127.0.0.1  aolgamedaily.122.2o7.net
127.0.0.1  aoljournals.122.2o7.net
127.0.0.1  aolmov.122.2o7.net
127.0.0.1  aolnews.122.2o7.net
127.0.0.1  aolnssearch.122.2o7.net
127.0.0.1  aolpf.122.2o7.net
127.0.0.1  aolpolls.122.2o7.net
127.0.0.1  aolsearch.122.2o7.net
127.0.0.1  aolshred.122.2o7.net
127.0.0.1  aolsports.122.2o7.net
127.0.0.1  aolsvc.122.2o7.net
127.0.0.1  aolswitch.122.2o7.net
127.0.0.1  aoltruveo.122.2o7.net
127.0.0.1  aoltmz.122.2o7.net
127.0.0.1  aolturnercnnmoney.122.2o7.net
127.0.0.1  aolturnersi.122.2o7.net
127.0.0.1  aoluk.122.2o7.net
127.0.0.1  aolvideo.122.2o7.net
127.0.0.1  aolwinamp.122.2o7.net
127.0.0.1  aolwbautoblog.122.2o7.net
127.0.0.1  aolwbcinema.122.2o7.net
127.0.0.1  aolwbdnlsq.122.2o7.net
127.0.0.1  aolwbengadget.122.2o7.net
127.0.0.1  aolwbgadling.122.2o7.net
127.0.0.1  aolwbluxist.122.2o7.net
127.0.0.1  aolwbtvsq.122.2o7.net
127.0.0.1  aolwbpspfboy.122.2o7.net
127.0.0.1  aolwpmq.122.2o7.net
127.0.0.1  aolwpnscom.122.2o7.net
127.0.0.1  aolwpnswhatsnew.112.2o7.net
127.0.0.1  apdigitalorgovn.112.2o7.net
127.0.0.1  apdigitalorg.112.2o7.net
127.0.0.1  apnonline.112.2o7.net
127.0.0.1  aumoautomotivectl.112.2o7.net
127.0.0.1  aumocarsbelowinvoice.112.2o7.net
127.0.0.1  aumointernetautoguidecom.112.2o7.net
127.0.0.1  aumonewcarcom.112.2o7.net
127.0.0.1  aumotradeinvaluecom.112.2o7.net
127.0.0.1  autobytel.112.2o7.net
127.0.0.1  autobytelcorppopup.112.2o7.net
127.0.0.1  autoanythingcom.112.2o7.net
127.0.0.1  autoscout24.112.2o7.net
127.0.0.1  autoweb.112.2o7.net
127.0.0.1  avon.112.2o7.net
127.0.0.1  babycentercom.112.2o7.net
127.0.0.1  bellglobemediapublishing.122.2o7.net
127.0.0.1  bertelwissenprod.122.2o7.net
127.0.0.1  bet.122.2o7.net
127.0.0.1  betterhg.112.2o7.net
127.0.0.1  bigpond.122.2o7.net
127.0.0.1  bizjournals.112.2o7.net
127.0.0.1  blockbuster.112.2o7.net
127.0.0.1  blockbustercom.112.2o7.net
127.0.0.1  bnkr8dev.112.2o7.net
127.0.0.1  boostmobile.112.2o7.net
127.0.0.1  brightcove.112.2o7.net
127.0.0.1  businessweekpoc.112.2o7.net
127.0.0.1  buycom.122.2o7.net
127.0.0.1  byubroadcast.112.2o7.net
127.0.0.1  canwest.112.2O7.net
127.0.0.1  canwestdose.112.2o7.net
127.0.0.1  capecodonlinecom.112.2o7.net
127.0.0.1  care2.112.2o7.net
127.0.0.1  carlsonradisson.112.2o7.net
127.0.0.1  cartoonnetwork.122.2o7.net
127.0.0.1  cbc.122.2o7.net
127.0.0.1  cbmsn.112.2o7.net
127.0.0.1  cbglobal.112.2O7.net
127.0.0.1  cbs.112.2o7.net #[SpySweeper.Spy.Cookie]
127.0.0.1  cbscom.112.2O7.net
127.0.0.1  cbsnfl.112.2O7.net
127.0.0.1  cbspgatour.112.2o7.net
127.0.0.1  cbsspln.112.2O7.net
127.0.0.1  ccrgaviscom.112.2o7.net
127.0.0.1  chacha.112.2o7.net
127.0.0.1  chchoice.112.2o7.net
127.0.0.1  cnhienid.122.2o7.net
127.0.0.1  chghowardjohnson.112.2o7.net
127.0.0.1  chgsupereight.112.2o7.net
127.0.0.1  chgwyndham.112.2o7.net
127.0.0.1  chicagosuntimes.122.2o7.net
127.0.0.1  chumtv.122.2o7.net
127.0.0.1  ciaoshopcouk.122.2o7.net
127.0.0.1  ciaoshopit.122.2o7.net
127.0.0.1  classmatescom.112.2o7.net
127.0.0.1  cmpdotnetjunkiescom.112.2o7.net
127.0.0.1  cmpglobalvista.112.2o7.net
127.0.0.1  cmtvia.112.2o7.net
127.0.0.1  cnetaustralia.122.2o7.net
127.0.0.1  cneteurope.122.2O7.net
127.0.0.1  cnetnews.112.2o7.net
127.0.0.1  cnettech.112.2O7.net
127.0.0.1  cnetzdnet.112.2o7.net
127.0.0.1  cnheagletribune.112.2o7.net
127.0.0.1  cnhiautovertical.122.2o7.net
127.0.0.1  cnhibatesvilleheraldtribune.122.2o7.net
127.0.0.1  cnhinewsservicedev.122.2o7.net
127.0.0.1  cnhirecordeagle.122.2o7.net
127.0.0.1  cnn.122.2O7.net
127.0.0.1  cnnglobal.122.2O7.net
127.0.0.1  cnocanoecaprod.112.2o7.net
127.0.0.1  computerworldcom.112.2o7.net
127.0.0.1  conpst.112.2o7.net
127.0.0.1  corelcom.112.2o7.net
127.0.0.1  coreluk.112.2o7.net
127.0.0.1  couponchief.122.2o7.net
127.0.0.1  coxhsi.112.2o7.net
127.0.0.1  coxnetmasterglobal.112.2o7.net
127.0.0.1  csoonlinecom.112.2o7.net
127.0.0.1  ctvcrimelibrary.112.2o7.net
127.0.0.1  ctvmaincom.112.2o7.net
127.0.0.1  ctvsmokinggun.112.2O7.net
127.0.0.1  ctvtsgtv.112.2o7.net
127.0.0.1  cwportal.112.2o7.net
127.0.0.1  cxociocom.112.2o7.net
127.0.0.1  cxocomdev.112.2o7.net
127.0.0.1  dealnews.122.2o7.net
127.0.0.1  detelegraaf.112.2o7.net
127.0.0.1  dexonline.112.2o7.net
127.0.0.1  dgcontentglobal.112.2o7.net
127.0.0.1  dhsmarthouse.122.2O7.net
127.0.0.1  digitalhomediscountptyltd.122.2o7.net
127.0.0.1  disccglobal.112.2o7.net
127.0.0.1  divx.112.2o7.net
127.0.0.1  dixonscouk.112.2o7.net
127.0.0.1  dmvguidecom.112.2o7.net
127.0.0.1  donred.112.2o7.net
127.0.0.1  donmer.112.2o7.net
127.0.0.1  donval.112.2o7.net
127.0.0.1  dotstermydomain.112.2O7.net
127.0.0.1  dowjones.122.2o7.net
127.0.0.1  eaeacom.112.2o7.net
127.0.0.1  eagamesuk.112.2o7.net
127.0.0.1  eaglemiles.112.2o7.net
127.0.0.1  eapogocom.112.2o7.net
127.0.0.1  earthlinkcom.122.2o7.net
127.0.0.1  earthlnkcom.122.2o7.net
127.0.0.1  earthlnkpsplive.122.2o7.net
127.0.0.1  edietsmain.112.2o7.net
127.0.0.1  edmundscom.112.2o7.net
127.0.0.1  efashionsolutions.122.2o7.net
127.0.0.1  enterprisenewsmedia.122.2o7.net
127.0.0.1  entrepreneur.122.2o7.net
127.0.0.1  entrepreneurpoc.122.2O7.net
127.0.0.1  eplans.112.2o7.net
127.0.0.1  eurostar.122.2o7.net
127.0.0.1  evepdcharleston.112.2o7.net
127.0.0.1  evepdaggiesports.112.2o7.net
127.0.0.1  evepdbrazossports.112.2o7.net
127.0.0.1  evepdeagledev.112.2o7.net
127.0.0.1  ewscorpuschristi.112.2o7.net
127.0.0.1  ewsmemphis.112.2o7.net
127.0.0.1  ewsnaples.112.2o7.net
127.0.0.1  ewsventura.112.2o7.net
127.0.0.1  expedia1.112.2o7.net
127.0.0.1  expedia6vt.112.2o7.net
127.0.0.1  expedia8.112.2o7.net
127.0.0.1  f2nbt.112.2o7.net
127.0.0.1  f2nsmh.112.2o7.net
127.0.0.1  f2ntheage.112.2o7.net
127.0.0.1  fbfredericksburgcom.112.2o7.net
127.0.0.1  figlobal.112.2o7.net
127.0.0.1  forbesattache.112.2o7.net
127.0.0.1  forbescom.112.2o7.net
127.0.0.1  ford.112.2o7.net
127.0.0.1  foxamw.112.2o7.net
127.0.0.1  foxcom.112.2o7.net
127.0.0.1  foxidol.112.2o7.net
127.0.0.1  furnlevitz.112.2o7.net
127.0.0.1  furniturecom.112.2o7.net
127.0.0.1  gateway.122.2o7.net
127.0.0.1  geosign.112.2o7.net
127.0.0.1  gifastcompanycom.112.2o7.net
127.0.0.1  gjfastcompanycom.112.2o7.net
127.0.0.1  giftscom.122.2o7.net
127.0.0.1  gntbcstkare.112.2o7.net
127.0.0.1  gntbcstksdk.112.2o7.net
127.0.0.1  gntbcstkthv.112.2o7.net
127.0.0.1  gntbcstkxtv.112.2o7.net
127.0.0.1  gntbcstwbir.112.2o7.net
127.0.0.1  gntbcstwfmy.112.2o7.net
127.0.0.1  gntbcstwkyc.112.2o7.net
127.0.0.1  gntbcstwlbz.112.2o7.net
127.0.0.1  gntbcstwmaz.112.2o7.net
127.0.0.1  gntbcstwcsh.112.2o7.net
127.0.0.1  gntbcstwltx.112.2o7.net
127.0.0.1  gntbcstwtlv.112.2o7.net
127.0.0.1  gntbcstwtsp.112.2o7.net
127.0.0.1  gntbcstwusa.112.2o7.net
127.0.0.1  gntbcstwxia.112.2o7.net
127.0.0.1  gntbcstwzzm.112.2o7.net
127.0.0.1  gntbcstglobal.112.2o7.net
127.0.0.1  gntbcstkusa.112.2o7.net
127.0.0.1  gourmetgiftbaskets.112.2o7.net
127.0.0.1  gpaper105.112.2o7.net
127.0.0.1  gpaper107.112.2o7.net
127.0.0.1  gpaper108.112.2o7.net
127.0.0.1  gpaper109.112.2o7.net
127.0.0.1  gpaper110.112.2O7.net
127.0.0.1  gpaper112.112.2o7.net
127.0.0.1  gpaper114.112.2O7.net
127.0.0.1  gpaper115.112.2o7.net
127.0.0.1  gpaper116.112.2o7.net
127.0.0.1  gpaper117.112.2o7.net
127.0.0.1  gpaper119.112.2O7.net
127.0.0.1  gpaper120.112.2o7.net
127.0.0.1  gpaper121.112.2O7.net
127.0.0.1  gpaper122.112.2o7.net
127.0.0.1  gpaper123.112.2O7.net
127.0.0.1  gpaper124.112.2O7.net
127.0.0.1  gpaper125.112.2o7.net
127.0.0.1  gpaper127.112.2o7.net
127.0.0.1  gpaper128.112.2o7.net
127.0.0.1  gpaper131.112.2o7.net
127.0.0.1  gpaper133.112.2o7.net
127.0.0.1  gpaper134.112.2o7.net
127.0.0.1  gpaper135.112.2o7.net
127.0.0.1  gpaper136.112.2O7.net
127.0.0.1  gpaper137.112.2o7.net
127.0.0.1  gpaper138.112.2o7.net
127.0.0.1  gpaper139.112.2o7.net
127.0.0.1  gpaper140.112.2o7.net
127.0.0.1  gpaper141.112.2o7.net
127.0.0.1  gpaper142.112.2o7.net
127.0.0.1  gpaper143.112.2o7.net
127.0.0.1  gpaper144.112.2o7.net
127.0.0.1  gpaper145.112.2O7.net
127.0.0.1  gpaper147.112.2o7.net
127.0.0.1  gpaper149.112.2O7.net #[eTrust.Tracking.Cookie]
127.0.0.1  gpaper150.112.2o7.net
127.0.0.1  gpaper151.112.2o7.net
127.0.0.1  gpaper152.112.2o7.net
127.0.0.1  gpaper156.112.2o7.net
127.0.0.1  gpaper157.112.2o7.net
127.0.0.1  gpaper158.112.2O7.net
127.0.0.1  gpaper160.112.2o7.net
127.0.0.1  gpaper161.112.2o7.net
127.0.0.1  gpaper162.112.2o7.net
127.0.0.1  gpaper163.112.2o7.net
127.0.0.1  gpaper164.112.2o7.net
127.0.0.1  gpaper166.112.2o7.net
127.0.0.1  gpaper167.112.2o7.net
127.0.0.1  gpaper168.112.2o7.net
127.0.0.1  gpaper169.112.2o7.net
127.0.0.1  gpaper170.112.2o7.net
127.0.0.1  gpaper171.112.2o7.net
127.0.0.1  gpaper172.112.2o7.net
127.0.0.1  gpaper173.112.2o7.net
127.0.0.1  gpaper174.112.2o7.net
127.0.0.1  gpaper175.112.2o7.net
127.0.0.1  gpaper176.112.2o7.net
127.0.0.1  gpaper177.112.2o7.net
127.0.0.1  gpaper178.112.2o7.net
127.0.0.1  gpaper180.112.2o7.net
127.0.0.1  gpaper183.112.2o7.net
127.0.0.1  gpaper184.112.2o7.net
127.0.0.1  gpaper185.112.2O7.net
127.0.0.1  gpaper186.112.2o7.net
127.0.0.1  gpaper187.112.2o7.net
127.0.0.1  gpaper190.112.2o7.net
127.0.0.1  gpaper194.112.2o7.net
127.0.0.1  gpaper195.112.2o7.net
127.0.0.1  gpaper196.112.2o7.net
127.0.0.1  gpaper197.112.2o7.net
127.0.0.1  gpaper199.112.2O7.net
127.0.0.1  gpaper201.112.2o7.net
127.0.0.1  gpaper202.112.2o7.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  gpaper204.112.2O7.net
127.0.0.1  gpaper211.112.2o7.net
127.0.0.1  gpaper214.112.2o7.net
127.0.0.1  gpaper218.112.2o7.net
127.0.0.1  gpaper223.112.2o7.net
127.0.0.1  gpaper246.112.2o7.net
127.0.0.1  gpapercareer.112.2o7.net
127.0.0.1  hallmarkibmcom.112.2o7.net
127.0.0.1  harrahscom.112.2o7.net
127.0.0.1  harpo.122.2o7.net
127.0.0.1  hchrmain.112.2o7.net
127.0.0.1  hearstmagazines.112.2o7.net
127.0.0.1  heavycom.122.2o7.net
127.0.0.1  hertz.122.2o7.net
127.0.0.1  highbeam.122.2o7.net
127.0.0.1  homestore.122.2o7.net
127.0.0.1  hphqglobal.112.2o7.net
127.0.0.1  hswmedia.122.2o7.net
127.0.0.1  imc2.122.2o7.net
127.0.0.1  imeem.112.2o7.net
127.0.0.1  incisivemedia.112.2o7.net
127.0.0.1  infratotalduicom.122.2O7.net
127.0.0.1  intelcorpchan.112.2o7.net
127.0.0.1  intelcorperror.112.2o7.net
127.0.0.1  intelcorpsupp.112.2o7.net
127.0.0.1  interland.122.2o7.net
127.0.0.1  instadia.112.2o7.net
127.0.0.1  itmedia.122.2o7.net
127.0.0.1  iusacomlive.112.2o7.net
127.0.0.1  ivillageglobal.112.2o7.net
127.0.0.1  jetbluepkgcs.112.2o7.net
127.0.0.1  jijsonline.112.2o7.net
127.0.0.1  jijsonline.122.2o7.net
127.0.0.1  jiwtmj.122.2o7.net
127.0.0.1  jmsyap.112.2o7.net
127.0.0.1  johnlewis.112.2o7.net
127.0.0.1  jrcdelcotimescom.122.2O7.net
127.0.0.1  jrcom.112.2o7.net
127.0.0.1  journalregistercompany.122.2o7.net
127.0.0.1  kaboose.112.2o7.net
127.0.0.1  kbbmain.112.2o7.net
127.0.0.1  lab88inc.112.2o7.net
127.0.0.1  laxnws.112.2o7.net #[WebBug]
127.0.0.1  laxprs.112.2o7.net
127.0.0.1  laxpsd.112.2o7.net
127.0.0.1  laxwht.122.2o7.net
127.0.0.1  laxwht.112.2o7.net
127.0.0.1  leeenterprises.112.2o7.net
127.0.0.1  ldsfch.112.2o7.net
127.0.0.1  livedealcom.112.2o7.net
127.0.0.1  mailtribunecom.112.2o7.net
127.0.0.1  mapscom2.112.2o7.net
127.0.0.1  marketlive.122.2o7.net
127.0.0.1  marksandspencer.122.2o7.net
127.0.0.1  mattressusa.122.2o7.net
127.0.0.1  maxim.122.2o7.net
127.0.0.1  mcclatchy.112.2o7.net
127.0.0.1  mdjacksonville.112.2O7.net
127.0.0.1  mdpparents.112.2o7.net
127.0.0.1  mdwjuneau.112.2o7.net
127.0.0.1  mdwsavannah.112.2o7.net
127.0.0.1  mediabistro.112.2o7.net
127.0.0.1  mediabistrocom.112.2o7.net
127.0.0.1  mediamatters.112.2o7.net
127.0.0.1  meetupdev.122.2O7.net
127.0.0.1  memberservicesinc.122.2o7.net
127.0.0.1  metacafe.122.2o7.net
127.0.0.1  mgdothaneagle.112.2o7.net
127.0.0.1  mghickoryrecord.112.2o7.net
127.0.0.1  mgjournalnow.112.2O7.net
127.0.0.1  mgwsav.112.2o7.net
127.0.0.1  mngitwincities.112.2o7.net
127.0.0.1  mgtbo.112.2O7.net
127.0.0.1  mgtbopanels.112.2O7.net
127.0.0.1  mgtimesdispatch.112.2o7.net
127.0.0.1  mgwcbd.112.2o7.net
127.0.0.1  mgwnct.112.2O7.net
127.0.0.1  mgwsls.112.2O7.net
127.0.0.1  microsofteup.112.2o7.net #[Panda.Spyware:Cookie/Microsofte]
127.0.0.1  microsoftoffice.112.2o7.net
127.0.0.1  microsoftwga.112.2o7.net
127.0.0.1  microsoftuk.122.2o7.net
127.0.0.1  microsoftwlmailmkt.112.2o7.net
127.0.0.1  microsoftwlmessengermkt.112.2o7.net
127.0.0.1  midala.112.2o7.net
127.0.0.1  midar.112.2o7.net
127.0.0.1  midcru.112.2o7.net
127.0.0.1  midsen.112.2o7.net
127.0.0.1  mkcthehomemarketplace.112.2o7.net
127.0.0.1  mkt10.122.2o7.net
127.0.0.1  mlbatlanta.112.2o7.net
127.0.0.1  mlbcincinnati.112.2o7.net
127.0.0.1  mlbcom.112.2o7.net
127.0.0.1  mlbglobal.112.2o7.net
127.0.0.1  mlbsanfrancisco.112.2o7.net
127.0.0.1  mlsglobal.112.2o7.net
127.0.0.1  mngidailybreeze.112.2o7.net
127.0.0.1  mngislctrib.112.2o7.net
127.0.0.1  mngisv.112.2o7.net
127.0.0.1  morningnewsonline.112.2o7.net
127.0.0.1  mseupwinxpfam.112.2o7.net
127.0.0.1  mngidmn.112.2O7.net
127.0.0.1  mngimercurynews.112.2o7.net
127.0.0.1  msna1com.112.2o7.net
127.0.0.1  msnaccountservices.112.2o7.net
127.0.0.1  msnbcom.112.2o7.net
127.0.0.1  msneshopbase.112.2o7.net
127.0.0.1  msninvite.112.2o7.net
127.0.0.1  msninviteprod.112.2O7.net
127.0.0.1  msnlivefavorites.112.2o7.net
127.0.0.1  msnmercom.112.2o7.net
127.0.0.1  msnmercustacqprod.112.2o7.net
127.0.0.1  msnportalaunews.112.2O7.net
127.0.0.1  msnportalbeetoffice2007.112.2o7.net
127.0.0.1  msnportalhome.112.2O7.net
127.0.0.1  msnportalgame.112.2O7.net
127.0.0.1  msnportallatino.112.2O7.net
127.0.0.1  msnportalmsgboardsrvc.112.2O7.net
127.0.0.1  msntrademarketing.112.2o7.net
127.0.0.1  msnwinonecare.112.2o7.net #[Windows OneCare]
127.0.0.1  msnportal.112.2o7.net #[SpySweeper.Spy.Cookie]
127.0.0.1  msnportallive.112.2O7.net
127.0.0.1  msnservices.112.2o7.net
127.0.0.1  mssbcprod.112.2o7.net
127.0.0.1  mswlspcmktdev.112.2O7.net
127.0.0.1  multiply.112.2o7.net
127.0.0.1  mxmacromedia.112.2o7.net
127.0.0.1  myfamilyancestry.112.2o7.net
127.0.0.1  nasdaqdev.122.2O7.net
127.0.0.1  natgeoedit.112.2o7.net
127.0.0.1  natgeoeditcom.112.2o7.net
127.0.0.1  natgeoglobal.112.2o7.net
127.0.0.1  natgeonavcom.112.2o7.net
127.0.0.1  natgeonews.112.2o7.net
127.0.0.1  natgeongkidsmagccom.112.2o7.net
127.0.0.1  natgeongmcom.112.2o7.net
127.0.0.1  natgeopeopleplaces.112.2o7.net
127.0.0.1  natgeotravelermagcom.112.2o7.net
127.0.0.1  nbcuniversal.122.2o7.net
127.0.0.1  neber.112.2o7.net
127.0.0.1  nebnr.112.2o7.net
127.0.0.1  nielsen.112.2o7.net
127.0.0.1  networksolutions.112.2o7.net
127.0.0.1  newsinteractive.112.2o7.net
127.0.0.1  newsok.112.2o7.net
127.0.0.1  newstimeslivecom.112.2o7.net
127.0.0.1  nikefootball.112.2o7.net
127.0.0.1  nikefootballglobal.112.2o7.net
127.0.0.1  nikegoddess.112.2o7.net
127.0.0.1  nikehome.112.2o7.net
127.0.0.1  nikerunning.112.2o7.net
127.0.0.1  nikerunningglobal.112.2o7.net
127.0.0.1  njmvc.112.2o7.net
127.0.0.1  nmanchorage.112.2o7.net
127.0.0.1  nmbakersfieldca.112.2o7.net
127.0.0.1  nmcomnancomedia.112.2o7.net
127.0.0.1  nmeprod.122.2O7.net
127.0.0.1  nmfresno.112.2o7.net
127.0.0.1  nmhiltonhead.112.2o7.net
127.0.0.1  nmmerced.112.2o7.net
127.0.0.1  nmminneapolis.112.2o7.net
127.0.0.1  nmraleigh.112.2o7.net
127.0.0.1  nmrockhill.112.2o7.net
127.0.0.1  nmsacramento.112.2O7.net
127.0.0.1  nortelcom.112.2o7.net
127.0.0.1  northwestairlines.112.2o7.net
127.0.0.1  novellcom.112.2o7.net
127.0.0.1  nsdldlese.112.2o7.net
127.0.0.1  newyorkmagazine.112.2o7.net
127.0.0.1  nytbglobe.112.2O7.net
127.0.0.1  nytrflorence.112.2o7.net
127.0.0.1  nytrgainesville.112.2o7.net
127.0.0.1  nytrhendersonville.112.2o7.net
127.0.0.1  nytrlakeland.112.2o7.net
127.0.0.1  nytrlexington.112.2o7.net
127.0.0.1  nytrocala.112.2o7.net
127.0.0.1  nytrsantarosa.112.2o7.net
127.0.0.1  nytrsarasota.112.2o7.net
127.0.0.1  nytrtuscaloosa.112.2o7.net
127.0.0.1  nytrworcester.112.2o7.net
127.0.0.1  nyttechnology.112.2O7.net
127.0.0.1  oberonincredig.112.2o7.net
127.0.0.1  omniture.112.2o7.net #[McAfee.Cookie-Omniture]
127.0.0.1  omniturecom.112.2o7.net
127.0.0.1  omniturebanners.112.2o7.net
127.0.0.1  omniscbt.112.2o7.net
127.0.0.1  onlinegurupopularsitecom.112.2o7.net
127.0.0.1  oodpreprod.122.2o7.net
127.0.0.1  oraclecom.112.2o7.net
127.0.0.1  ottacknet.112.2o7.net
127.0.0.1  overturecom.112.2o7.net
127.0.0.1  pandasoftware.112.2o7.net
127.0.0.1  partygaming.122.2o7.net
127.0.0.1  partygamingglobal.122.2O7.net
127.0.0.1  pch.122.2o7.net
127.0.0.1  pctoolscom.112.2o7.net
127.0.0.1  petakfc.112.2o7.net
127.0.0.1  petamain.112.2o7.net
127.0.0.1  planetout.122.2o7.net
127.0.0.1  pldev.112.2o7.net
127.0.0.1  plsoyfoods.112.2o7.net
127.0.0.1  poacprod.122.2o7.net
127.0.0.1  poconorecordcom.112.2o7.net
127.0.0.1  powellsbooks.122.2o7.net
127.0.0.1  poweronemedia.122.2o7.net
127.0.0.1  premiumtv.122.2o7.net
127.0.0.1  primediabusiness.122.2o7.net
127.0.0.1  primestarmagazine.112.2o7.net
127.0.0.1  prnewswire.122.2o7.net
127.0.0.1  primemensfitness.112.2o7.net
127.0.0.1  pulkauaiworld.112.2o7.net
127.0.0.1  questiacom.112.2o7.net
127.0.0.1  qwestfull.112.2o7.net
127.0.0.1  rainbowmedia.122.2o7.net
127.0.0.1  rakuten.112.2o7.net
127.0.0.1  rebtelnetworks.112.2o7.net
127.0.0.1  recordeaglecom.112.2o7.net
127.0.0.1  recordnetcom.112.2o7.net
127.0.0.1  recordonlinecom.112.2o7.net
127.0.0.1  registercom.122.2o7.net
127.0.0.1  reunioncom.112.2o7.net
127.0.0.1  riptownmedia.122.2o7.net
127.0.0.1  riverdeep.112.2o7.net
127.0.0.1  rmgparcelforcecom.112.2o7.net
127.0.0.1  rmgroyalmailcom.112.2o7.net
127.0.0.1  rrpartners.122.2o7.net
127.0.0.1  safaribooks.112.2o7.net
127.0.0.1  saksfifthavenue.122.2o7.net
127.0.0.1  saxoconcordmonitor.122.2o7.net
127.0.0.1  saxogreensboro.122.2o7.net
127.0.0.1  saxoorklamedia.122.2o7.net
127.0.0.1  saxorutland.122.2o7.net
127.0.0.1  saxotelegraph.122.2o7.net
127.0.0.1  saxowesterncommunications.122.2o7.net
127.0.0.1  sbsblukgov.112.2o7.net
127.0.0.1  scottrade.112.2o7.net
127.0.0.1  seacoastonlinecom.112.2o7.net
127.0.0.1  searskmcom.112.2o7.net
127.0.0.1  sento.122.2o7.net
127.0.0.1  schaeffers.112.2o7.net
127.0.0.1  shawnewspapers.112.2o7.net
127.0.0.1  shopping.112.2o7.net
127.0.0.1  skyauction.122.2O7.net
127.0.0.1  slbbbcom.112.2o7.net
127.0.0.1  sltravelcom.112.2o7.net
127.0.0.1  smibs.112.2o7.net
127.0.0.1  smpopmech.112.2o7.net
127.0.0.1  smwww.112.2O7.net
127.0.0.1  snapfish.112.2o7.net
127.0.0.1  sonycorporate.122.2o7.net
127.0.0.1  southcoasttodaycom.112.2o7.net
127.0.0.1  sportingnews.122.2o7.net
127.0.0.1  sprintglobal.112.2o7.net
127.0.0.1  starz.122.2o7.net
127.0.0.1  stpetersburgtimes.122.2o7.net
127.0.0.1  stubhub.122.2o7.net
127.0.0.1  stylincom.112.2o7.net
127.0.0.1  sunglobal.112.2o7.net
127.0.0.1  sympmsnglobalen.112.2o7.net
127.0.0.1  sympmsnmusic.112.2o7.net
127.0.0.1  tbstv.112.2o7.net
127.0.0.1  techreview.112.2o7.net
127.0.0.1  tel3adv.112.2o7.net
127.0.0.1  telefloracom.112.2o7.net
127.0.0.1  thayhoteldelcoronado.112.2o7.net
127.0.0.1  thayhiltonlongisland.112.2o7.net
127.0.0.1  thayvenetian.112.2o7.net
127.0.0.1  thedailystarcom.112.2o7.net
127.0.0.1  thgalecom.112.2o7.net
127.0.0.1  thelibraryofcongress.122.2o7.net
127.0.0.1  thestar.122.2O7.net
127.0.0.1  thestardev.122.2O7.net
127.0.0.1  thinkgeek.112.2o7.net
127.0.0.1  thomasvillefurniture.122.2o7.net
127.0.0.1  timecom.112.2o7.net
127.0.0.1  timecom.122.2o7.net
127.0.0.1  timeew.122.2o7.net
127.0.0.1  timeessence.122.2o7.net
127.0.0.1  timefortune.112.2o7.net
127.0.0.1  timelife.122.2o7.net
127.0.0.1  timepeople.122.2o7.net
127.0.0.1  timeteenpeople.122.2o7.net
127.0.0.1  tgn.122.2o7.net
127.0.0.1  tmstoyota.112.2o7.net
127.0.0.1  torstardigital.122.2o7.net
127.0.0.1  trailblazers.122.2o7.net
127.0.0.1  tribuneinteractive.122.2o7.net
127.0.0.1  trinitymirror.112.2o7.net
127.0.0.1  turnerclassic.112.2o7.net
127.0.0.1  turnersports.112.2o7.net
127.0.0.1  uolfreeservers.112.2o7.net
127.0.0.1  uoljunocom2.112.2o7.net
127.0.0.1  uolnetzeronet2.112.2o7.net
127.0.0.1  uolphotosite.112.2o7.net
127.0.0.1  upi.112.2o7.net
127.0.0.1  usatoday1.112.2o7.net
127.0.0.1  tbsveryfunnyads.112.2o7.net
127.0.0.1  vcomdeepdiscount.112.2o7.net
127.0.0.1  vcommerce.112.2o7.net
127.0.0.1  verisignwildcard.112.2o7.net #[sitefinder.verisign.com]
127.0.0.1  viaaddictingclips.112.2o7.net
127.0.0.1  viaaddictinggames.112.2o7.net
127.0.0.1  viacomedycentralrl.112.2o7.net
127.0.0.1  viagametrailers.112.2o7.net
127.0.0.1  vialogoonline.112.2o7.net
127.0.0.1  vialogorollup.112.2o7.net
127.0.0.1  viamtvcom.112.2o7.net
127.0.0.1  viashockwave.112.2o7.net
127.0.0.1  viamtvukdev.112.2o7.net
127.0.0.1  viaquiz.112.2o7.net
127.0.0.1  viavh1com.112.2o7.net
127.0.0.1  viay2m.112.2o7.net
127.0.0.1  victoriaadvocate.112.2o7.net
127.0.0.1  vintacom.112.2o7.net
127.0.0.1  vintadream.112.2o7.net
127.0.0.1  viamtvuk.112.2o7.net
127.0.0.1  volkswagen.122.2o7.net
127.0.0.1  walmartcom.112.2o7.net
127.0.0.1  wbextecd.112.2o7.net
127.0.0.1  wbnews.112.2o7.net
127.0.0.1  wbprocurement.112.2o7.net
127.0.0.1  whitecastle.122.2o7.net
127.0.0.1  winmpmain.112.2O7.net #[Windows MarketPlace]
127.0.0.1  wissende.122.2o7.net
127.0.0.1  worldnowboston.112.2o7.net
127.0.0.1  wpni.112.2o7.net
127.0.0.1  wrigley.122.2o7.net
127.0.0.1  wweconsumer.112.2o7.net
127.0.0.1  wwecorp2.112.2o7.net
127.0.0.1  xhealth.112.2o7.net
127.0.0.1  xhealthmobiltools.112.2o7.net
127.0.0.1  yellcom.122.2o7.net
127.0.0.1  yrkdsp.112.2O7.net
127.0.0.1  zag.112.2O7.net
127.0.0.1  zango.112.2o7.net
127.0.0.1  zdau-builder.122.2O7.net
127.0.0.1  ziffdavisfilefront.112.2o7.net
127.0.0.1  ziffdavisglobal.112.2o7.net
127.0.0.1  ziffdavispennyarcade.112.2o7.net
127.0.0.1  stats.esomniture.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.omniture.com
127.0.0.1  www.touchclarity.com
# [Omniture via Misc Sites]
127.0.0.1  omni.amerisuites.com #[amerisuites.com.112.2o7.net]
127.0.0.1  metrics.apple.com #[appleglobal.112.2o7.net]
127.0.0.1  metrics.azfamily.com
127.0.0.1  n.betus.com
127.0.0.1  mtrcs.bizrate.com #[bizrate.com.122.2o7.net]
127.0.0.1  n.bodybuilding.com
127.0.0.1  om.businessweek.com
127.0.0.1  stats.cartoonnetwork.com
127.0.0.1  om.dowjoneson.com
127.0.0.1  metrics.eldiariony.com
127.0.0.1  m.evite.com
127.0.0.1  om.expedia.com
127.0.0.1  metrics.fox11az.com
127.0.0.1  metric.infoworld.com
127.0.0.1  stats.investors.com
127.0.0.1  metrics.kgw.com
127.0.0.1  metrics.khou.com
127.0.0.1  metrics.krem.com
127.0.0.1  metrics.ktvb.com
127.0.0.1  metrics.kvue.com
127.0.0.1  metrics.mysanantonio.com
127.0.0.1  stats.nascar.com
127.0.0.1  metrics.nba.com #[nba.com.112.2o7.net]
127.0.0.1  oimg.nbcuni.com
127.0.0.1  img.omnistats.net
127.0.0.1  om.philly.com
127.0.0.1  om.pokerlistings.com
127.0.0.1  mtrcs.popcap.com
127.0.0.1  wa.proflowers.com
127.0.0.1  metrics.quick6.com
127.0.0.1  metrics.quickdfw.com
127.0.0.1  omtrkpix.rd.com
127.0.0.1  om.sfgate.com
127.0.0.1  om.symantec.com
127.0.0.1  tc.symantec.com
127.0.0.1  n.thestar.com
127.0.0.1  m.trb.com
127.0.0.1  om.usnews.com
127.0.0.1  metrics.washingtonpost.com
127.0.0.1  std.o.webmd.com #[webmdglobal.122.2o7.net][Web Bug]
127.0.0.1  metrics.wfaa.com
127.0.0.1  metric.wtop.com
127.0.0.1  instadia.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www.instadia.net
# [OptInRealBig.com, LLC][Scott Richter]
127.0.0.1  aimphuck.com
127.0.0.1  www.aimphuck.com #[HJTH.Look2Me]
127.0.0.1  c4c01.com
127.0.0.1  www.cpaempire.com
127.0.0.1  www.cpaempire.net
127.0.0.1  ekmas.com
127.0.0.1  www.empire404.com
127.0.0.1  http602.com
127.0.0.1  megaiconsite.com
127.0.0.1  www.megaiconsite.com
127.0.0.1  login.tracking101.com #[directtrack.com][Ewido.TrackingCookie.Tracking101]
127.0.0.1  optinbig.com #[SiteAdvisor.optinbig.com]
127.0.0.1  www.optinbig.com
# [Ottavio Bizzio Group][Alexey Smirnoff]
127.0.0.1  www.bytecode.biz
127.0.0.1  www.drabland.net
127.0.0.1  www.insorg.net
127.0.0.1  my-traff.net
127.0.0.1  russianerofoto.com
# [Oversee.net Group]
127.0.0.1  www.comnetcn.com
127.0.0.1  searchportal.cq2.net
127.0.0.1  domainsponsor.com #[Ad-Aware.Tracking.Cookie][WIPO.D2006-0523]
127.0.0.1  images.domainsponsor.com
127.0.0.1  landing.domainsponsor.com #[Microsoft.Typo-Patrol]
127.0.0.1  searchportal.domainsponsor.com
127.0.0.1  spi.domainsponsor.com
127.0.0.1  www.domainsponsor.com #[Panda.Spyware:Cookie/DomainSponsor]
127.0.0.1  inboxrewards.com
127.0.0.1  www.inboxrewards.com
127.0.0.1  dp.information.com
127.0.0.1  search.information.com
127.0.0.1  searchportal.information.com #[Panda.Spyware:Cookie/Searchportal]
127.0.0.1  sp2.information.com
127.0.0.1  www.information.com
127.0.0.1  track.newslettersponsor.com
127.0.0.1  www.newslettersponsor.com
127.0.0.1  oversee.net
127.0.0.1  blizzard.thor.oversee.net
127.0.0.1  domainsponsor.oversee.net
127.0.0.1  popupsponsor.com #[Parasite.ClientMan]
127.0.0.1  ads.popupsponsor.com #[SunBelt.PopupSponsor]
127.0.0.1  mediatrack.popupsponsor.com
127.0.0.1  view.popupsponsor.com
127.0.0.1  www.popupsponsor.com
127.0.0.1  proredirect.com
127.0.0.1  www.proredirect.com
127.0.0.1  revenue.net
127.0.0.1  ads.revenue.net #[SunBelt.Revenue.net]
127.0.0.1  ads.kw.revenue.net
127.0.0.1  ads0.revenue.net
127.0.0.1  ads1.revenue.net #[SpySweeper.Spy.Cookie][Adware-Adlogix]
127.0.0.1  ads2.revenue.net
127.0.0.1  ads4.revenue.net
127.0.0.1  count.revenue.net #[popupsponsor.com]
127.0.0.1  images.revenue.net
127.0.0.1  mediatrack.revenue.net #[Tenebril.Tracking.Cookie]
127.0.0.1  view.revenue.net
127.0.0.1  www.revenue.net
127.0.0.1  domainimages.targetwords.com
127.0.0.1  domainimages2.targetwords.com
127.0.0.1  domainlanding.targetwords.com
127.0.0.1  ie.targetwords.com
127.0.0.1  images.targetwords.com
127.0.0.1  impress.targetwords.com
127.0.0.1  search.targetwords.com
127.0.0.1  targetwords.com
127.0.0.1  www.targetwords.com
127.0.0.1  ehg-overseenet.hitbox.com
# [Parked.com]
127.0.0.1  images.parked.com
127.0.0.1  www.searchnut.com
# [Peter Emonds][Alla Lakaeva][WorldToStart B.V.]
127.0.0.1  bannersandpopups.com #[TROJ_DLOADER.ACJ][Troj/Winsysba-C]
127.0.0.1  www.bannersandpopups.com #[Adware.SP2Update]
127.0.0.1  click.dotcomtoolbar.com #[SPW_DCTOOLBAR.A]
127.0.0.1  www.dotcomtoolbar.com #[Spyware.Dotcomtoolbar]
127.0.0.1  www.easywww.info #[Troj/Weasyw-A][McAfee.QHosts-2]
127.0.0.1  www.exetrafflc.com
127.0.0.1  findthewebsiteyouneed.com #[Trojan JAVA_NEEDY.A]
127.0.0.1  click.findthewebsiteyouneed.com
127.0.0.1  searchbar.findthewebsiteyouneed.com #[BackDoor.Afcore.AL]
127.0.0.1  www.findthewebsiteyouneed.com #[Trojan-Downloader.Win32.VB.aiy]
127.0.0.1  www.globaladvertisingservices.info
127.0.0.1  internetadvertisingcompany.biz
127.0.0.1  www.internetadvertisingcompany.biz
127.0.0.1  www.internetadvertisingservices.info
127.0.0.1  linksummary.com
127.0.0.1  click.linksummary.com
127.0.0.1  demon1.linksummary.com
127.0.0.1  demon2.linksummary.com
127.0.0.1  redirect.linksummary.com
127.0.0.1  searchbar.linksummary.com
127.0.0.1  www.linksummary.com
127.0.0.1  www.mediahighway.net
127.0.0.1  www.moneyadvertisingservices.info
127.0.0.1  www.nonameforthisdomain.com #[TR/StartPage.AW.1][Troj/Winsysba-C]
127.0.0.1  www.revenueadvertisingservices.info
127.0.0.1  www.sp2msupdateresearch.com #[Adware.SP2Update][TROJ_DLOADER.ACJ]
127.0.0.1  yoursearchbar.com
127.0.0.1  www.yoursearchbar.com
127.0.0.1  yourstartingpage.com
127.0.0.1  www.yourstartingpage.com #[SunBelt.Tro.YourStartingPage]
127.0.0.1  www.worldwideadvertisingservices.info
# [Phil Vizzaccaro]
127.0.0.1  www.123counts.com
127.0.0.1  hitslink.com
127.0.0.1  counter.hitslink.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  counter2.hitslink.com #[Ewido.TrackingCookie.Hitslink]
127.0.0.1  www2.hitslink.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.hitslink.com #[SunBelt.hitslink.com]
127.0.0.1  loc1.hitsprocessor.com
127.0.0.1  www.toolshack.com
# [PointRoll][Gannett]
127.0.0.1  pointroll.com
127.0.0.1  ads.pointroll.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ev.ads.pointroll.com
127.0.0.1  ami.pointroll.com #[p.mii.instacontent.net]
127.0.0.1  clk.pointroll.com
127.0.0.1  media.pointroll.com #[Panda.Spyware:Cookie/PointRoll]
127.0.0.1  mirror.pointroll.com #[Ewido.TrackingCookie.Pointroll]
127.0.0.1  speed.pointroll.com #[a1343.g.akamai.net]
127.0.0.1  t.pointroll.com
127.0.0.1  track.pointroll.com #[eTrust.Tracking.Cookie]
127.0.0.1  www.pointroll.com
# [positive web creations]
127.0.0.1  www.247lyrics.com
127.0.0.1  www.lyricsdomain.com
127.0.0.1  www.negativebeats.com #[Downloader.Small]
127.0.0.1  positivebeats.com #[JS/TrojanClicker.Linker.M]
127.0.0.1  www.positivebeats.com
# [Pressflex]
127.0.0.1  b.blogads.com
127.0.0.1  banners.blogads.com
127.0.0.1  banners2.blogads.com
127.0.0.1  c.blogads.com
127.0.0.1  cache.blogads.com
127.0.0.1  images2.blogads.com
127.0.0.1  st.blogads.com #[WebBug]
127.0.0.1  stat.blogads.com #[WebBug]
127.0.0.1  weblog.blogads.com
127.0.0.1  www.blogads.com
127.0.0.1  adz.liberianobserver.com
127.0.0.1  ads.pressflex.com
127.0.0.1  adserver.pressflex.com #[SiteAdvisor.liberianobserver.com]
127.0.0.1  fishadz.pressflex.net
# [Privacy Protect][Parking Service]
127.0.0.1  images.bnmq.com
127.0.0.1  www.bnmq.com
127.0.0.1  search.in
# [Qool Aid LLC][GFC International][Velebit Communications]
127.0.0.1  qoolaid.mygeek.com
127.0.0.1  web-nexus.net #[Adw.Web-Nexus.WebNexusAdServer]
127.0.0.1  ax.web-nexus.net #[TROJ_QOOLAID.R]
127.0.0.1  dl.web-nexus.net #[eTrust.Win32.Qoologic]
127.0.0.1  stech.web-nexus.net #[Trojan-Downloader.Win32.Qoologic.p]
127.0.0.1  www.web-nexus.net
# [QTK Internet]
127.0.0.1  www.atomictime.net
127.0.0.1  eu-adcenter.net
127.0.0.1  thinknyc.eu-adcenter.net
127.0.0.1  ugo.eu-adcenter.net
127.0.0.1  www.infa.net
127.0.0.1  sweetbabes.com #[atomictime.net]
127.0.0.1  www.sweetbabes.com
# [Quadrogram, LLC][MemoryWatcher][Win32.Memwatch]
127.0.0.1  client.contextual.esyndicate.com #[Adware.eSyndicate]
127.0.0.1  queue.jmnad1.com #[Adware.eSyndicate]
127.0.0.1  www.jmnad1.com
127.0.0.1  www.memorywatcher.com #[TROJ_PEPER.A]
127.0.0.1  rads01.quadrogram.com #[Adware.Quadro]
127.0.0.1  queue.searchreslt.com
127.0.0.1  www.searchreslt.com #[Adware-SideSearch]
127.0.0.1  www.search-result.net
127.0.0.1  www.smartsearch.com.au
# [Rambler Internet Holdings][Tracking Service]
127.0.0.1  ad.rambler.ru #[SecuritySpace.WebBug]
127.0.0.1  ad2.rambler.ru
127.0.0.1  ad3.rambler.ru
127.0.0.1  counter.rambler.ru #[SunBelt.Rambler.ru]
127.0.0.1  id.rambler.ru
127.0.0.1  images.rambler.ru
127.0.0.1  info-images.rambler.ru
127.0.0.1  scnt.rambler.ru
127.0.0.1  top100.rambler.ru
127.0.0.1  topshop-counter.rambler.ru
127.0.0.1  top100-images.rambler.ru
# [Rampell Software][Email Tracker]
127.0.0.1  didtheyreadit.com
127.0.0.1  www.didtheyreadit.com
127.0.0.1  xpostmail.com
# [Rampid Interactive]
127.0.0.1  outwar.com #[SunBelt.Outwar Adware Launcher]
127.0.0.1  fabar.outwar.com
127.0.0.1  sigil.outwar.com
127.0.0.1  torax.outwar.com
127.0.0.1  www.outwar.com #[Trojan.Win32.VB.iy][ADW_OUTWAR.A]
127.0.0.1  ads.rampidads.com #[eTrust.Tracking.Cookie]
127.0.0.1  main.rampidads.com
127.0.0.1  www.rampidads.com
# [Razor Media][DestinyWeb][N-Light]
127.0.0.1  www.paypergig.com
127.0.0.1  www.razormedia.net
127.0.0.1  www.trafficneeds.com
# [RealCast Media LLC][Jambo Media Llc]
127.0.0.1  realbannerads.com
127.0.0.1  ads.realcastmedia.com #[directtrack.com]
127.0.0.1  www.realcastmedia.com
127.0.0.1  www.realtextads.com
# [24/7 Real Media Inc]
127.0.0.1  ads.247wsr.com
127.0.0.1  banner.clickfinders.com #[SunBelt.ClickFinders]
127.0.0.1  search.clickfinders.com
127.0.0.1  tracking.clickfinders.com
127.0.0.1  www.clickfinders.com
127.0.0.1  dealcollect.insightfirst.com
127.0.0.1  lifetimecollect.insightfirst.com
127.0.0.1  thedeal.insightfirst.com
127.0.0.1  unitedcollect.insightfirst.com
127.0.0.1  adv.247realmedia.com #[McAfee.Cookie-247realmedia]
127.0.0.1  adv0005.247realmedia.com
127.0.0.1  adv0035.247realmedia.com
127.0.0.1  adv0054.247realmedia.com
127.0.0.1  betcollect.247realmedia.com
127.0.0.1  ftbusinesscollect.247realmedia.com
127.0.0.1  gmtvcollect.247realmedia.com
127.0.0.1  imagec05.247realmedia.com #[c2.mii.instacontent.net]
127.0.0.1  imagec07.247realmedia.com
127.0.0.1  imagec08.247realmedia.com
127.0.0.1  imagesn02.247realmedia.com #[s5.mii.instacontent.net]
127.0.0.1  ipro.247realmedia.com
127.0.0.1  looksmartcollect.247realmedia.com
127.0.0.1  lshlcollect.247realmedia.com
127.0.0.1  lseducationcollect.247realmedia.com #[LookSmart]
127.0.0.1  lsmusiccollect.247realmedia.com
127.0.0.1  lssportscollect.247realmedia.com
127.0.0.1  lycos.247realmedia.com
127.0.0.1  lycoscollect.247realmedia.com
127.0.0.1  mediafr.247realmedia.com
127.0.0.1  mediauk.247realmedia.com
127.0.0.1  medicinenetcollect.247realmedia.com
127.0.0.1  network-ca.247realmedia.com
127.0.0.1  nx-adv0035.247realmedia.com
127.0.0.1  oas-eu.247realmedia.com
127.0.0.1  oasc02.247realmedia.com #[Panda.Spyware:Cookie]
127.0.0.1  oasc03.247realmedia.com
127.0.0.1  oasc03012.247realmedia.com
127.0.0.1  oasc03049.247realmedia.com
127.0.0.1  oasc04025.247realmedia.com
127.0.0.1  oasc04052.247realmedia.com
127.0.0.1  oasc04062.247realmedia.com
127.0.0.1  oasc05024.247realmedia.com #[MVPS.Criteria]
127.0.0.1  oasc06006.247realmedia.com
127.0.0.1  oasc04.247realmedia.com
127.0.0.1  pittlive.247realmedia.com
127.0.0.1  postgazette.247realmedia.com
127.0.0.1  postgazettecollect.247realmedia.com
127.0.0.1  singletraining56.247realmedia.com
127.0.0.1  retaildirect.realmedia.com
127.0.0.1  villagevoicecollect.247realmedia.com
127.0.0.1  ads.realmedia.com.br
127.0.0.1  icover.realmedia.com
127.0.0.1  lycos.realmedia.com
127.0.0.1  lycoscollect.realmedia.com
127.0.0.1  mserv1.realmedia.com
127.0.0.1  network.realmedia.com #[SpySweeper.Spy.Cookie]
127.0.0.1  oad.realmedia.com
127.0.0.1  oas-central.realmedia.com
127.0.0.1  pub.realmedia.fr
127.0.0.1  ad.realmedia.co.kr
127.0.0.1  tech.realmedia.co.kr
127.0.0.1  ads.realmedia.ro
127.0.0.1  tracking.247search.com
127.0.0.1  realmedia-a592.d4p.net
# [24/7 Real Media via various Services]
127.0.0.1  ads.accountingweb.com
127.0.0.1  ads.chumcity.com
127.0.0.1  ads.epi.es
127.0.0.1  ads.jacksonville.com
127.0.0.1  ads.juneauempire.com
127.0.0.1  ads.letemps.ch
127.0.0.1  ads.miniclip.com
127.0.0.1  ads.mrtones.com
127.0.0.1  ads.nwsource.com
127.0.0.1  ads.pennnet.com
127.0.0.1  ads.r-kimedia.co.uk
127.0.0.1  ads.savannahnow.com
127.0.0.1  ads.seattletimes.com
127.0.0.1  a3.suntimes.com
127.0.0.1  ads.telecinco.es
127.0.0.1  ads.thedeal.com
127.0.0.1  ads.timesunion.com
127.0.0.1  ads.trinitymirror.co.uk
127.0.0.1  adsrv.dispatch.com #[oasc05a.247realmedia.com]
127.0.0.1  insightfirst.oxygen.com
127.0.0.1  insightxe.accuweather.com #[accuweathercollect.247realmedia.com]
127.0.0.1  insightxe.artistdirect.com
127.0.0.1  insightxe.fayettevillenc.com
127.0.0.1  insightxe.investors.com
127.0.0.1  insightxe.pittsburghlive.com #[pittlivecollect.247realmedia.com]
127.0.0.1  insightxe-ssl.pittsburghlive.com
127.0.0.1  insightxe.reference.com #[referencecollect.247realmedia.com]
127.0.0.1  insightxe.sportswar.com
127.0.0.1  insightxe.starbulletin.com
127.0.0.1  insightxe.thephoenix.com
127.0.0.1  insightxe.vtsgonline.com
127.0.0.1  insightxe.washtimes.com #[washtimescollect.247realmedia.com]
127.0.0.1  mjx.ads.nwsource.com #[oasc04a.247realmedia.com]
127.0.0.1  oascentral.123greetings.com
127.0.0.1  oascentral.abclocal.go.com
127.0.0.1  oascentral.activeathlete.net
127.0.0.1  oascentral.adage.com
127.0.0.1  oascentral.adcritic.com
127.0.0.1  oascentral.atlanticnewsnet.ca
127.0.0.1  oascentral.alladultchannel.com
127.0.0.1  oas.ameinfo.com
127.0.0.1  oascentral.hosted.ap.org
127.0.0.1  oascentral.artistdirect.com
127.0.0.1  oascentral.autoweek.com
127.0.0.1  oascentral.blackenterprise.com
127.0.0.1  oascentral.blogher.org
127.0.0.1  oascentral.btobonline.com
127.0.0.1  oascentral.bigfishgames.com
127.0.0.1  oascentral.bostonherald.com
127.0.0.1  oascentral.broadway.com
127.0.0.1  oascentral.businessweek.com
127.0.0.1  oascentral.buy.com
127.0.0.1  oascentral.buysell.com
127.0.0.1  oascentral.capecodonline.com
127.0.0.1  oascentral.cardomain.com
127.0.0.1  oascentral.careerbuilder.com
127.0.0.1  realmedia.channel4.com
127.0.0.1  oascentral.charleston.net
127.0.0.1  oascentral.chicagobusiness.com
127.0.0.1  oascentral.chron.com
127.0.0.1  oascentral.clearchannel.com
127.0.0.1  oascentral.comcast.net
127.0.0.1  oascentral.courttv.com
127.0.0.1  oascentral.covers.com
127.0.0.1  oascentral.crainsdetroit.com
127.0.0.1  oascentral.crimelibrary.com
127.0.0.1  oascentral.cruisecritic.com
127.0.0.1  oascentral.dailybreeze.com
127.0.0.1  oas.deejay.it
127.0.0.1  oascentral.discovery.com
127.0.0.1  oascentral.emedicine.com
127.0.0.1  oascentral.entrepreneur.com
127.0.0.1  oascentral.fantasyplayers.com
127.0.0.1  oascentral.fayettevillenc.com
127.0.0.1  oascentral.freedom.com
127.0.0.1  oas.ftbusiness.com
127.0.0.1  oascentral.g4techtv.com
127.0.0.1  oascentral.gazette.com
127.0.0.1  oascentral.ggl.com
127.0.0.1  oascentral.gotriad.com
127.0.0.1  oascentral.greenevillesun.com
127.0.0.1  oascentral.hamptonroads.com
127.0.0.1  oascentral.highbeam.com
127.0.0.1  oascentral.hollywood.com
127.0.0.1  oascentral.inq7.net
127.0.0.1  oascentral.investmentnews.com
127.0.0.1  oascentral.investors.com
127.0.0.1  oascentral.katv.com
127.0.0.1  oascentral.kontraband.com
127.0.0.1  oascentral.lacitybeat.com
127.0.0.1  oascentral.law.com
127.0.0.1  oascentral.laweekly.com
127.0.0.1  oascentral.lifetimetv.com
127.0.0.1  oascentral.looksmart.com
127.0.0.1  oascentral.lycos.com
127.0.0.1  oascentral.mailtribune.com
127.0.0.1  oas.maktoob.com
127.0.0.1  oascentral.mayoclinic.com
127.0.0.1  oascentral.mediavillage.com
127.0.0.1  oascentral.metro.us
127.0.0.1  oascentral.miaminewtimes.com
127.0.0.1  oascentral.motherjones.com
127.0.0.1  oascentral.movietickets.com
127.0.0.1  oascentral.nashvillescene.com
127.0.0.1  oascentral.nerve.com
127.0.0.1  oascentral.newsmax.com
127.0.0.1  oascentral.news-record.com
127.0.0.1  oascentral.newtimesbpb.com
127.0.0.1  oascentral.newstimeslive.com
127.0.0.1  oascentral.nowtoronto.com
127.0.0.1  oascentral.ocweekly.com
127.0.0.1  oascentral.oxygen.com
127.0.0.1  oascentral.theonion.com
127.0.0.1  oascentral.onwisconsin.com
127.0.0.1  oascentral.oprah.com
127.0.0.1  oascentral.poconorecord.com
127.0.0.1  oascentral.pokerfan.com
127.0.0.1  oascentral.post-gazette.com
127.0.0.1  oascentral.pressdemocrat.com
127.0.0.1  oascentral.publicradio.org
127.0.0.1  oascentral.recordnet.com
127.0.0.1  oascentral.recordonline.com
127.0.0.1  oascentral.record-eagle.com
127.0.0.1  oascentral.redherring.com #[server down?]
127.0.0.1  oascentral.reference.com
127.0.0.1  oascentral.register.com
127.0.0.1  oascentral.registerguard.com
127.0.0.1  oas.repubblica.it
127.0.0.1  oas.rivals.com
127.0.0.1  oas.romandie-online.ch
127.0.0.1  oascentral.sciam.com
127.0.0.1  oascentral.seattleweekly.com
127.0.0.1  oas.sh3bwah.com
127.0.0.1  oascentral.sfgate.com
127.0.0.1  oascentral.sfweekly.com
127.0.0.1  oascentral.sina.com
127.0.0.1  oascentral.sovo.com
127.0.0.1  oascentral.sportswar.com
127.0.0.1  oascentral.sptimes.com
127.0.0.1  oascentral.s-t.com
127.0.0.1  oascentral.starbulletin.com
127.0.0.1  oascentral.stltoday.com
127.0.0.1  oas.sulekha.com
127.0.0.1  oascentral.suntimes.com
127.0.0.1  oascentral.superpages.com
127.0.0.1  oascentral.thechronicleherald.ca
127.0.0.1  oascentral.thehockeynews.com
127.0.0.1  oascentral.theintelligencer.net
127.0.0.1  oascentral.theonionavclub.com
127.0.0.1  oascentral.thephoenix.com
127.0.0.1  oascentral.thesmokinggun.com
127.0.0.1  oascentral.tmcnet.com
127.0.0.1  oascentral.traffic.com
127.0.0.1  oascentral.tnr.com
127.0.0.1  oascentral.upi.com
127.0.0.1  oascentral.verizononline.com
127.0.0.1  oascentral.videodome.com
127.0.0.1  oascentral.villagevoice.com
127.0.0.1  oascentral.virtualtourist.com
127.0.0.1  oascentral.wagerline.com
127.0.0.1  oascentral.walmartwom.com
127.0.0.1  oascentral.warcry.com
127.0.0.1  oascentral.washtimes.com
127.0.0.1  oascentral.wciv.com
127.0.0.1  oascentral.wjla.com
127.0.0.1  oascentral.yellowpages.com
127.0.0.1  werbung.metropool.ch #[eur56deliv.247realmedia.com]
127.0.0.1  www.rmfaceparty.com
127.0.0.1  a.windowsitpro.com #[oasc04a.247realmedia.com]
127.0.0.1  oascentral.wwe.com
# [Realtracker][Media Highway International]
127.0.0.1  realtracker.com
127.0.0.1  adserver1.realtracker.com #[SunBelt.RealTracker.com]
127.0.0.1  adserver2.realtracker.com
127.0.0.1  business.realtracker.com
127.0.0.1  free.realtracker.com
127.0.0.1  layout1.realtracker.com
127.0.0.1  project2.realtracker.com
127.0.0.1  talkcity.realtracker.com
127.0.0.1  tpl1.realtracker.com
127.0.0.1  tpl2.realtracker.com
127.0.0.1  web1.realtracker.com #[eTrust.Tracking.Cookie]
127.0.0.1  web2.realtracker.com #[SpySweeper.Spy.Cookie][MVPS.Criteria]
127.0.0.1  web4.realtracker.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  free1.usa.realtracker.com
127.0.0.1  www.realtracker.com
127.0.0.1  free1.realtrackernl.com
127.0.0.1  free.realtrackernl.com
127.0.0.1  11.rtcode.com
127.0.0.1  11.rtstats.com
127.0.0.1  www.nethit-free.nl
127.0.0.1  www.netpoll.nl
# [Relevence Marketing Group]
127.0.0.1  453searches.com #[SunBelt.UpMedia.Search]
127.0.0.1  cpv.453searches.com
127.0.0.1  directory.453searches.com #[Adware.Searchtool]
127.0.0.1  icons.453searches.com
127.0.0.1  more.453searches.com
127.0.0.1  app.asmartershopper.com
127.0.0.1  www.asmartershopper.com #[TR/Dldr.SmartShop.2]
127.0.0.1  checkin100.com #[SiteAdvisor.smutvidoftheday.com]
127.0.0.1  dist.checkin100.com #[W32/Adload.FPS]
127.0.0.1  checkin101.com
127.0.0.1  a.downloadmediacentral.com #[SiteAdvisor.myadultexplorer.com]
127.0.0.1  ads.downloadmediacentral.com
127.0.0.1  exe.downloadmediacentral.com
127.0.0.1  fpa.downloadmediacentral.com #[aff.primaryads.com][MVPS.Criteria]
127.0.0.1  img.downloadmediacentral.com
127.0.0.1  link.downloadmediacentral.com
127.0.0.1  media.downloadmediacentral.com #[Win32/TrojanDownloader.Agent.AUV]
127.0.0.1  www.downloadmediacentral.com
127.0.0.1  www.holdem-u.com
127.0.0.1  im4me.com
127.0.0.1  imforme.com #[Trojan.Downloader.Agent.CZ]
127.0.0.1  www.imforme.com
127.0.0.1  imfourme.com #[Downloader.Agent.GVB]
127.0.0.1  marksdailynews.com
127.0.0.1  marksdirtysecrets.com
127.0.0.1  mediaprovider.info #[Win32/TrojanDownloader.Agent.NJC]
127.0.0.1  light.mediaprovider.info #[getmirar.com]
127.0.0.1  myadultexplorer.com
127.0.0.1  client.myadultexplorer.com
127.0.0.1  www.myadultexplorer.com #[server down?]
127.0.0.1  onlyfreeadult.com
127.0.0.1  www.onlyfreeadult.com
127.0.0.1  puzzledesktop.com
127.0.0.1  client.puzzledesktop.com
127.0.0.1  sudoku.puzzledesktop.com
127.0.0.1  www.puzzledesktop.com #[Trojan.Downloader.Agent.CZ]
127.0.0.1  quickdatasearch.com
127.0.0.1  rapidinfosearch.com
127.0.0.1  relevancemarketingltd.com
127.0.0.1  www.relevancemarketingltd.com #[Trojan-Downloader.Win32.Agent.auv]
127.0.0.1  search.searchme100.com #[search.thinktarget.com]
127.0.0.1  searchme101.com
127.0.0.1  sense-expert.com
127.0.0.1  sense-pro.com
127.0.0.1  sense-super.com
127.0.0.1  sense-wonder.com
127.0.0.1  www.serverunavailab1e.com #[Adware.Searchtool]
127.0.0.1  super-context.com
127.0.0.1  swiftinfosearch.com
127.0.0.1  wonder-context.com #[Adware.Searchtool]
127.0.0.1  app.wonder-context.com
127.0.0.1  new.wonder-context.com
127.0.0.1  wonder-search.com
# [Retrostats]
127.0.0.1  www.groovystats.com
127.0.0.1  www.petstats.com
127.0.0.1  www.pridestats.com
127.0.0.1  www.retrostats.com
127.0.0.1  www.zodiacstats.com
# [Right Media, LLC][Yahoo]
127.0.0.1  content.yieldmanager.edgesuite.net
127.0.0.1  www.rightmedia.com #[McAfee.Cookie-Rightmedia][SpySweeper.Spy.Cookie]
127.0.0.1  content.rmxads.com #[content.yieldmanager.com]
127.0.0.1  optimizedby.rmxads.com
127.0.0.1  ad.yieldmanager.com #[Kephyr.PUP][MVPS.Criteria]
127.0.0.1  api.yieldmanager.com #[api.se.yieldmanager.com]
127.0.0.1  content.yieldmanager.com #[Panda.Spyware:Cookie/YieldManager]
127.0.0.1  my.yieldmanager.com #[Ewido.TrackingCookie.Yieldmanager]
# [Right Media - clones][208.67.64.0 - 208.67.71.255]
127.0.0.1  adserver.00web.com #[ad.yieldmanager.com]
127.0.0.1  content.91s.com #[content.yieldmanager.com]
127.0.0.1  ad.acceleratorusa.com
127.0.0.1  ad.adconsole.com #[ad.yieldmanager.com]
127.0.0.1  content.adconsole.com #[eXact Advertising]
127.0.0.1  ad.ad-flow.com #[ad.yieldmanager.com]
127.0.0.1  content.ad-flow.com #[content.yieldmanager.com]
127.0.0.1  my.admedian.com #[my.yieldmanager.com]
127.0.0.1  ad.adnetinteractive.com
127.0.0.1  content.adnetinteractive.com
127.0.0.1  ad.adserverplus.com
127.0.0.1  ad.adtegrity.net #[ad.yieldmanager.com]
127.0.0.1  content.adtegrity.net #[content.yieldmanager.com]
127.0.0.1  my.adtegrity.net #[my.yieldmanager.com]
127.0.0.1  my.aim4media.com #[my.yieldmanager.com]
127.0.0.1  ad.aimedia.com #[ad.yieldmanager.com]
127.0.0.1  content.aimedia.com #[content.yieldmanager.com]
127.0.0.1  content.attune.com #[content.yieldmanager.com]
127.0.0.1  ad.audible.fm #[ad.yieldmanager.com]
127.0.0.1  content.audible.fm #[content.yieldmanager.com]
127.0.0.1  ad.axill.com #[ad.yieldmanager.com]
127.0.0.1  content.axill.com #[content.yieldmanager.com]
127.0.0.1  ad.bannerconnect.net #[ad.yieldmanager.com]
127.0.0.1  content.bannerconnect.net #[content.yieldmanager.com]
127.0.0.1  ym.bannerconnect.net #[my.yieldmanager.com]
127.0.0.1  ads.bigad.com #[ad.yieldmanager.com]
127.0.0.1  content.bigad.com #[content.yieldmanager.com]
127.0.0.1  adserving.budsinc.com #[ad.yieldmanager.com]
127.0.0.1  ad.contentspecific.com
127.0.0.1  content.contentspecific.com
127.0.0.1  adserving.cpxinteractive.com #[ad.yieldmanager.com]
127.0.0.1  content.cpxinteractive.com #[content.yieldmanager.com]
127.0.0.1  reporting.cpxinteractive.com #[BudsInc]
127.0.0.1  ad.directanetworks.com #[ad.yieldmanager.com]
127.0.0.1  content.directanetworks.com #[content.yieldmanager.com]
127.0.0.1  content.fimnetwork.com
127.0.0.1  media.fimnetwork.com #[ad.yieldmanager.com]
127.0.0.1  ad.firstadsolution.com #[ad.yieldmanager.com]
127.0.0.1  content.firstadsolution.com #[content.yieldmanager.com]
127.0.0.1  ad.globalinteractive.com #[ad.yieldmanager.com]
127.0.0.1  content.globalinteractive.com #[content.yieldmanager.com]
127.0.0.1  ad.greenmarquee.com #[ad.yieldmanager.com]
127.0.0.1  ad.iconadserver.com #[ad.yieldmanager.com]
127.0.0.1  content.iconadserver.com
127.0.0.1  my.iconadserver.com #[my.yieldmanager.com]
127.0.0.1  ad.ireit.com #[ad.yieldmanager.com]
127.0.0.1  content.ireit.com #[content.yieldmanager.com]
127.0.0.1  content.joetec.net #[content.yieldmanager.com]
127.0.0.1  ad.joinaxxess.com #[ad.yieldmanager.com]
127.0.0.1  content.joinaxxess.com #[content.yieldmanager.com]
127.0.0.1  ads-rm.looksmart.com #[ad.yieldmanager.com]
127.0.0.1  ad.marketingsector.com #[ad.yieldmanager.com]
127.0.0.1  content.marketingsector.com #[content.yieldmanager.com]
127.0.0.1  my.marketingsector.com #[my.yieldmanager.com]
127.0.0.1  ad.media-servers.net #[ad.yieldmanager.com]
127.0.0.1  content.media-servers.net #[content.yieldmanager.com]
127.0.0.1  my.media-servers.net #[my.yieldmanager.com]
127.0.0.1  ad.mediaprecision.net #[ad.yieldmanager.com]
127.0.0.1  content.mediaprecision.net #[ClickSpring]
127.0.0.1  my.mediaprecision.net #[my.yieldmanager.com]
127.0.0.1  ad.motiveinteractive.com #[ad.yieldmanager.com]
127.0.0.1  content.motiveinteractive.com
127.0.0.1  delb.myspace.com #[ad.yieldmanager.com]
127.0.0.1  delb2.myspace.com #[media.fimnetwork.com]
127.0.0.1  ad.oinadserver.com #[ad.yieldmanager.com][McAfee.Adware-ClickSpring]
127.0.0.1  ad.realcastmedia.com #[ad.yieldmanager.com]
127.0.0.1  content.realcastmedia.com #[content.yieldmanager.com]
127.0.0.1  my.realcastmedia.com #[my.yieldmanager.com]
127.0.0.1  ad.reduxmedia.com #[ad.yieldmanager.com]
127.0.0.1  content.reduxmedia.com #[content.yieldmanager.com]
127.0.0.1  ad.scanmedios.com
127.0.0.1  content.scanmedios.com
127.0.0.1  ads.searchingbooth.com #[ad.yieldmanager.com]
127.0.0.1  adserver.sitesense.com #[ad.yieldmanager.com][Parking Service]
127.0.0.1  ad.thewheelof.com
127.0.0.1  content.thewheelof.com
127.0.0.1  ad.valencemedia.com #[ad.yieldmanager.com]
127.0.0.1  content.valencemedia.com #[content.yieldmanager.com]
127.0.0.1  content.womensforum.com
127.0.0.1  ad.xplusone.com
127.0.0.1  ad.yieldx.com #[ad.yieldmanager.com]
127.0.0.1  content.yieldx.com #[content.yieldmanager.com]
# [Rogue/Suspect Anti-Spyware Products]
127.0.0.1  www.1clickspyclean.com
127.0.0.1  www.3bsoftware.com #[Spyware Protection Pro]
127.0.0.1  6d-antivirus.com
127.0.0.1  www.6d-antivirus.com
127.0.0.1  antispydownloads.org
127.0.0.1  antispystorm.com #[Symantec.AntiSpyStorm]
127.0.0.1  secure.antispystorm.com
127.0.0.1  www.antispystorm.com
127.0.0.1  antiviruspcsuite.com #[SunBelt.AntivirusPCSuite]
127.0.0.1  sale.antiviruspcsuite.com
127.0.0.1  www.antiviruspcsuite.com
127.0.0.1  www.actualresearch.com
127.0.0.1  www.ad-purge.com #[thespywareshield.com]
127.0.0.1  www.adware-remover.net #[ADS Adware Remover]
127.0.0.1  www.adwarexeliminator.com
127.0.0.1  www.adwarespywareremoval.com
127.0.0.1  www.alphawipe.com
127.0.0.1  www.anti-viruses.net #[Symantec.TrojanGuarder]
127.0.0.1  avsystemcare.com #[Symantec.Adware.InstallProvider]
127.0.0.1  calc.avsystemcare.com
127.0.0.1  sale.avsystemcare.com
127.0.0.1  ykeeper.avsystemcare.com
127.0.0.1  www.avsystemcare.com #[Symantec.AVSystemCare]
127.0.0.1  www.codeclean.co.kr #[Adware-CodeClean][server down?]
127.0.0.1  www.contravirus.biz
127.0.0.1  contravirus.net
127.0.0.1  download1.contravirus.net
127.0.0.1  www.contravirus.net
127.0.0.1  contraviruspro.com
127.0.0.1  download1.contraviruspro.com
127.0.0.1  www.contraviruspro.com
127.0.0.1  copperheadsecurity.com
127.0.0.1  www.copperheadsecurity.com
127.0.0.1  curepcsolutions.com
127.0.0.1  www.curepcsolutions.com #[Symantec.CurePCSolution]
127.0.0.1  doctorcleaner.com #[SunBelt.Doctor Cleaner]
127.0.0.1  drcleaner.com
127.0.0.1  www.doctorcleaner.com
127.0.0.1  egeosoftware.com #[Adware.Win32.Privacy Crusader]
127.0.0.1  www.egeosoftware.com #[SiteAdvisor.egeosoftware.com]
127.0.0.1  etrust-spyware.com
127.0.0.1  www.etrust-spyware.com
127.0.0.1  gsiconcepts.com #[SecureMyPC]
127.0.0.1  www.gsiconcepts.com
127.0.0.1  installprovider.com #[Adware.InstallProvider]
127.0.0.1  download.installprovider.com
127.0.0.1  www.installprovider.com
127.0.0.1  www.isnake.net #[Symantec.SpyViper][Spyware.ISnake]
127.0.0.1  killspy.net #[Symantec.AntiVirusPro]
127.0.0.1  www.killspy.net
127.0.0.1  www.kazaap.org #[Symantec.Kazaap]
127.0.0.1  live-protect.com
127.0.0.1  www.live-protect.com #[Symantec.LiveProtect]
127.0.0.1  www.logiguard.com #[SpyPry]
127.0.0.1  www.malwareburn.com #[Symantec.MalwareBurn]
127.0.0.1  www.mycleanerpc.com #[Symantec.MyCleanerPC]
127.0.0.1  no-spy-ware.com #[login.tracking101.com]
127.0.0.1  www.oreware.com
127.0.0.1  www.pchealthplan.com #[Symantec.PCHealthPlan]
127.0.0.1  www.pcprivacysoftware.com #[Symantec.AdsAlert]
127.0.0.1  freepcsecure.com #[Win32/Adware.WinFixer]
127.0.0.1  www.freepcsecure.com #[SiteAdvisor.freepcsecure.com]
127.0.0.1  pc-prot.com
127.0.0.1  www.pc-prot.com
127.0.0.1  pcprivacytool.com #[Symantec.PCPrivacyTool]
127.0.0.1  shop.pcprivacytool.com
127.0.0.1  www.pcprivacytool.com
127.0.0.1  perfect-cleaner.com #[server down?]
127.0.0.1  www.perfect-cleaner.com
127.0.0.1  perfectcleaner2007.com #[Win32/Genetik]
127.0.0.1  www.perfectcleaner2007.com
127.0.0.1  www.pimasoft.com #[Spy Sniper][Ultimate-Spyware]
127.0.0.1  download.privacy-kit.com
127.0.0.1  evidence.privacy-kit.com
127.0.0.1  www.privacy-kit.com #[Symantec.PrivacyKit]
127.0.0.1  privacyprotector.com
127.0.0.1  go.privacyprotector.com #[ParetoLogic.PrivacyProtector]
127.0.0.1  jsp.privacyprotector.com
127.0.0.1  secure.privacyprotector.com
127.0.0.1  stats.privacyprotector.com
127.0.0.1  url.privacyprotector.com
127.0.0.1  www.privacyprotector.com #[Symantec.PrivacyProtector]
127.0.0.1  adware.privacy-solution.com
127.0.0.1  www.privacy-solution.com
127.0.0.1  www.professionalcash.com
127.0.0.1  quickcleaner.com
127.0.0.1  www.quickcleaner.com #[QCV6C030.Install]
127.0.0.1  rebrandsoftware.com
127.0.0.1  www.rebrandsoftware.com
127.0.0.1  redemptionengine.com #[SiteAdvisor.redemptionengine.com]
127.0.0.1  www.redemptionengine.com
127.0.0.1  rewardsengine.com
127.0.0.1  www.rewardsengine.com
127.0.0.1  www.scanspyware.net #[SiteAdvisor.scanspyware.net]
127.0.0.1  www.shareware4web.com
127.0.0.1  www.software4yoursuccess.com #[Froggie Scan]
127.0.0.1  solidlabs.com
127.0.0.1  www.solidlabs.com #[Symantec.SpywareAnnihilatorPro]
127.0.0.1  spyaway2007.com
127.0.0.1  www.spyaway2007.com
127.0.0.1  spywarebot.com
127.0.0.1  download.spywarebot.com
127.0.0.1  www.spywarebot.com
127.0.0.1  www.spybot-spyware-removal.com #[palsol.com]
127.0.0.1  spyferret.com #[OnlinePcFix.SpyFerret]
127.0.0.1  www.spyferret.com
127.0.0.1  www.spyfighter.com #[Symantec.SpyFighter]
127.0.0.1  spyinator.com
127.0.0.1  www.spyinator.com #[Symantec.Spyinator]
127.0.0.1  spy-kill.com
127.0.0.1  deluxe.spy-kill.com
127.0.0.1  www.spy-kill.com
127.0.0.1  download.spyonthis.net
127.0.0.1  www.spyonthis.net
127.0.0.1  spyshield.org
127.0.0.1  www.spyshield.org
127.0.0.1  www.spyvest.com
127.0.0.1  www.spyware-blaster-software.com
127.0.0.1  spycrush.com
127.0.0.1  www.spycrush.com #[Symantec.SpyCrush]
127.0.0.1  spywarecrusher.com
127.0.0.1  www.spywarecrusher.com
127.0.0.1  spywarecure.net
127.0.0.1  spyvampire.com
127.0.0.1  www.spyvampire.com
127.0.0.1  www.spywarecure.net
127.0.0.1  www.spywaredefense.com
127.0.0.1  www.spywareit.com
127.0.0.1  www.spywareremovalwizard.com #[Symantec.SpywareRemovalWizard]
127.0.0.1  spywarescrapper.com
127.0.0.1  www.spywarescrapper.com #[Symantec.SpywareScrapper]
127.0.0.1  www.spywarethis.com
127.0.0.1  adware.storesbiz.com
127.0.0.1  spywareremover.storebiz4u.com
127.0.0.1  startguard.net
127.0.0.1  www.startguard.net
127.0.0.1  www.storebiz4u.com
127.0.0.1  www.tekeffect.com
127.0.0.1  www.teosoft.biz
127.0.0.1  www.teosoft.com
127.0.0.1  secure.thepayonline.com #[winfixmaster.com]
127.0.0.1  www.thespywaredetective.com #[Symantec.TheSpywareDetective]
127.0.0.1  thespywareshield.com
127.0.0.1  www.thespywareshield.com
127.0.0.1  www.trackzapper.com
127.0.0.1  www.truesuite.com #[TrueWatch]
127.0.0.1  trustedprotection.com
127.0.0.1  sale.trustedprotection.com
127.0.0.1  www.trustedprotection.com
127.0.0.1  ultimatecleaner.com
127.0.0.1  www.ultimatecleaner.com #[UCInstall Class]
127.0.0.1  www.win-fix.com
127.0.0.1  winfixmaster.com
127.0.0.1  www.winfixmaster.com
127.0.0.1  www.winkeeper.net
127.0.0.1  www.winsos.com
127.0.0.1  winxdefender.com #[Symantec.WinXDefender]
127.0.0.1  download.winxdefender.com #[FraudTool.Win32.WinXDefender.a]
127.0.0.1  www.winxdefender.com
127.0.0.1  www.x-conspywaredestroyer.com
127.0.0.1  www.your-soft.com #[Symantec.TrojanGuarder]
127.0.0.1  www.zzztech.com
# [Alexandre Ivanov][Popandopulos Ltd][DiabloCompany]
127.0.0.1  diaremover.com
127.0.0.1  www.diaremover.com
127.0.0.1  magicantispy.com #[Win32/Adware.SpySheriff]
127.0.0.1  www.magicantispy.com #[Symantec.MagicAntiSpy]
127.0.0.1  pestwiper.com #[Norman.W32/Spywad.ER][Rogue/Suspect]
127.0.0.1  www.pestwiper.com #[NOD32.Win32/Adware.SpySheriff.variant]
127.0.0.1  spysheriff.com #[SunBelt.SpySheriff]
127.0.0.1  www.spysheriff.com #[McAfee.Adware-SpySheriff]
127.0.0.1  spy-shredder.com
127.0.0.1  scanner.spy-shredder.com #[WildCard DNS]
127.0.0.1  www.spy-shredder.com
127.0.0.1  www.spy-sheriff.com #[McAfee.StartPage-IH]
127.0.0.1  www.spytrooper.com #[Panda.Adware/Spytrooper][eTrust.Win32.Puper]
127.0.0.1  www.spy-trooper.com
127.0.0.1  spyware-cash.com
127.0.0.1  www.spyware-cash.com
127.0.0.1  spywareno.com #[searchterror.com]
127.0.0.1  www.spywareno.com #[Downloader-ACZ]
# [Armor2net Software]
127.0.0.1  www.armor2net.com #[Rogue/Suspect]
127.0.0.1  www.spywarekiller.net #[Rogue/Suspect]
127.0.0.1  www.totalfax.net
# [Clint Brown]
127.0.0.1  www.easyerase.com #[Rogue/Suspect]
127.0.0.1  www.easyspywarescanner.com
127.0.0.1  www.seekways.com
# [Concordia][Backpackers]
127.0.0.1  scanandclean.com #[UnSpyPC clone]
127.0.0.1  www.scanandclean.com 
127.0.0.1  www.unspypc.com #[Symantec.UnSpyPC][McAfee.UnSpyPC]
# [Elite Concepts]
127.0.0.1  www.adwarespy.com #[Symantec.AdwareSpy]
127.0.0.1  www.buildtraffic.com
127.0.0.1  www.buildtrafficx.com
127.0.0.1  www.eliteconcepts.com
127.0.0.1  www.loggerx.com
127.0.0.1  www.spywarespy.com #[Rogue/Suspect]
# [eSunSoft Technologies]
127.0.0.1  www.esunsofttechnologies.com #[Symantec.MyBugFreePc]
# [ibisweb corp]
127.0.0.1  spyware-sweeper.com
127.0.0.1  www.spyware-sweeper.com
# [Innovagest 2000 SL][OBAKE LIMITED][Alison Popandopulos]
127.0.0.1  www.1stantivirus.com #[Rogue/Suspect][Symantec.1stAntiVirus]
127.0.0.1  download.alfacleaner.com #[Trojan.Alemod.B][Downloader.Harnig]
127.0.0.1  license.alfacleaner.com
127.0.0.1  www.alfacleaner.com #[SunBelt.PUS.AlfaCleaner]
127.0.0.1  www.anti-virus-pro.com
127.0.0.1  secure.innovagest2000.com
127.0.0.1  www.innovagest2000.com #[Rogue/Suspect]
127.0.0.1  secure.isoftpay.com
127.0.0.1  malwarealarm.com
127.0.0.1  scanner.malwarealarm.com
127.0.0.1  www.malwarealarm.com #[Win32/Adware.SpySheriff]
127.0.0.1  www.spycontra.com
127.0.0.1  www.spydeface.com #[Rogue/Suspect]
127.0.0.1  www.virushammer.com
# [Insomniac Industries]
127.0.0.1  www.spyware-cop.com
127.0.0.1  www.spywarekilla.com
# [Mandel Enterprises][David Da Silva]
127.0.0.1  adwarexterminator.com #[AdWare.ToolBar.AlexaBar.A]
127.0.0.1  www.adwarexterminator.com
127.0.0.1  adwarepatrol.com #[Rogue/Suspect]
127.0.0.1  www.adwarepatrol.com
127.0.0.1  adwaredeluxe.com #[Rogue/Suspect]
127.0.0.1  www.adwaredeluxe.com
127.0.0.1  adwareremover.ws
127.0.0.1  adwaresafety.com
127.0.0.1  alertspy.com #[Rogue/Suspect][ibill.com]
127.0.0.1  antispyadvanced.com
127.0.0.1  www.antispyadvanced.com
127.0.0.1  antivirusadvance.com
127.0.0.1  www.antivirusadvance.com
127.0.0.1  antiviruspremium.com
127.0.0.1  www.antiviruspremium.com
127.0.0.1  antivirusprotector.com
127.0.0.1  www.antivirusprotector.com
127.0.0.1  antivirusprotectionsite.com
127.0.0.1  www.antivirusprotectionsite.com
127.0.0.1  doctoradware.com #[Rogue/Suspect]
127.0.0.1  doctoradwarepro.com #[Rogue/Suspect][Symantec.DoctorAdwarePro]
127.0.0.1  www.etdscanner.com #[Rogue/Suspect]
127.0.0.1  expertcash.com
127.0.0.1  flashdollars.com
127.0.0.1  www.flashdollars.com
127.0.0.1  imp3download.com
127.0.0.1  www.microantivirus.com
127.0.0.1  microantivirusxp.com
127.0.0.1  www.pestbot.com #[Rogue/Suspect]
127.0.0.1  pestprotector.com
127.0.0.1  platinumpartner.com
127.0.0.1  www.platinumpartner.com
127.0.0.1  popprotection.com
127.0.0.1  registryrepair.ws
127.0.0.1  spyadvanced.com #[Rogue/Suspect]
127.0.0.1  spydestroy.com
127.0.0.1  www.spydestroy.com
127.0.0.1  spywareremoval.ws #[SpwareRemoval]
127.0.0.1  spywarexp.com #[Rogue/Suspect]
127.0.0.1  unknownip.com
127.0.0.1  www.unknownip.com
127.0.0.1  virusscansite.com
127.0.0.1  www.virusscansite.com
# [Marko Novakovic]
127.0.0.1  msoftware.info
127.0.0.1  secure.msoftware.info
127.0.0.1  www.msoftware.info
127.0.0.1  www.repair-registry.net
127.0.0.1  download.scanandrepair.com #[Symantec.ScanandRepair]
127.0.0.1  www.scanandrepair.com #[Rogue/Suspect]
# [Neospace Group]
127.0.0.1  neospaceonline.com
127.0.0.1  servicebuys.com
# [Nous-Tech Solutions]
127.0.0.1  www.softwarereferral.com
127.0.0.1  ucleaner.biz
127.0.0.1  www.ucleaner.biz
127.0.0.1  ucleaner.com
127.0.0.1  secure.ucleaner.com
127.0.0.1  www.ucleaner.com #[Win32/Adware.UltimateCleaner]
127.0.0.1  ucleaner.info
127.0.0.1  www.ucleaner.info
127.0.0.1  ucleaner.net
127.0.0.1  www.ucleaner.net
127.0.0.1  ucleaner.org
127.0.0.1  www.ucleaner.org
127.0.0.1  udefender.biz
127.0.0.1  udefender.com #[eTrust.Ultimate Defender]
127.0.0.1  www.udefender.com #[Win32/Adware.UltimateDefender]
127.0.0.1  www.udefender.net #FraudTool.Win32.UltimateDefender.c]
127.0.0.1  udefender.org
127.0.0.1  ufixer.com
127.0.0.1  www.ufixer.com #[Win32/Adware.UltimateFixer]
# [PAL Solutions Ltd]
127.0.0.1  www.jcspyware-remover.com #[Rogue/Suspect]
127.0.0.1  palsol.com #[Rogue/Suspect]
127.0.0.1  www.palsol.com
127.0.0.1  www.palsol.net
127.0.0.1  www.palsoftwareworks.com
127.0.0.1  www.palspywareremover.com
127.0.0.1  www.spy-spyware.com
127.0.0.1  www.spywaretek.com #[Rogue/Suspect]
# [PCSecurityShield]
127.0.0.1  pcsecurityshield.com #[Rogue/Suspect]
127.0.0.1  banners.pcsecurityshield.com
127.0.0.1  clickbank.pcsecurityshield.com
127.0.0.1  downloads.pcsecurityshield.com
127.0.0.1  partners.pcsecurityshield.com #[directtrack.com]
127.0.0.1  regnow.pcsecurityshield.com
127.0.0.1  shop.pcsecurityshield.com
127.0.0.1  trk.pcsecurityshield.com #[affiliatetracking.net]
127.0.0.1  www.pcsecurityshield.com #[SiteAdvisor.pcsecurityshield.com]
# [Santa Monica Networks Inc]
127.0.0.1  www.keywordmarketplace.com #[SiteAdvisor.keywordmarketplace.com]
127.0.0.1  ads.kmpads.com #[Ewido.TrackingCookie.Kmpads]
127.0.0.1  ads.smni.com #[SpySweeper.Spy.Cookie]
127.0.0.1  static.smni.com #[Panda.Spyware:Cookie/Santa Monica networks]
# [Secure Computer, LLC][Gary Preston]
127.0.0.1  www.errorfixer.com #[SunBelt.Errorfixer]
127.0.0.1  www.errorfixerdownload.com
127.0.0.1  www.myerrorfixer.com
127.0.0.1  www.myspywarecleaner.com #[Rogue/Suspect]
127.0.0.1  www.spywarecleanerdownload2.com
# [SunShine Ltd][U-12 Group][David Taylor]
127.0.0.1  www.almanah.biz
127.0.0.1  almanah1.biz
127.0.0.1  www.almanah1.biz
127.0.0.1  antispydns.biz
127.0.0.1  www.antispydns.biz
127.0.0.1  dragracers.biz
127.0.0.1  malwarewipe.com #[eTrust.MalwareWipe]
127.0.0.1  dl.malwarewipe.com
127.0.0.1  dl2.malwarewipe.com #[Symantec.MalwareWipe]
127.0.0.1  dl3.malwarewipe.com
127.0.0.1  dl4.malwarewipe.com
127.0.0.1  dl5.malwarewipe.com
127.0.0.1  dl9.malwarewipe.com
127.0.0.1  partners.malwarewipe.com
127.0.0.1  www.malwarewipe.com #[McAfee.Adware-Malwarewipe]
127.0.0.1  malwarewiped.com #[Win32/Adware.MalwareWipe]
127.0.0.1  dl.malwarewiped.com
127.0.0.1  dl2.malwarewiped.com
127.0.0.1  dl3.malwarewiped.com
127.0.0.1  dl4.malwarewiped.com
127.0.0.1  dl5.malwarewiped.com
127.0.0.1  dl9.malwarewiped.com
127.0.0.1  www.malwarewiped.com
127.0.0.1  www.malwarewipesupport.com #[download2.spyaxe.net]
127.0.0.1  www.malwarewipeupdate.com
127.0.0.1  securecheck.biz
127.0.0.1  spyaxe.biz
127.0.0.1  www.spyaxe.biz
127.0.0.1  spyaxe.com #[Trojan.Spaxe][eTrust.Win32/Spax]
127.0.0.1  download.spyaxe.com
127.0.0.1  www.spyaxe.com #[Rogue/Suspect][McAfee.Adware-Spyaxe]
127.0.0.1  spyaxe.net #[eTrust.Win32.Puper]
127.0.0.1  download2.spyaxe.net #[malwarewipesupport.com]
127.0.0.1  download3.spyaxe.net
127.0.0.1  download4.spyaxe.net
127.0.0.1  download5.spyaxe.net
127.0.0.1  download6.spyaxe.net #[malwarewipeupdate.com]
127.0.0.1  download7.spyaxe.net
127.0.0.1  download8.spyaxe.net
127.0.0.1  img.spyaxe.net
127.0.0.1  www.spyaxe.net #[eTrust.Win32/Spax]
127.0.0.1  spyaxesupport.com
127.0.0.1  www.spyaxeupdate.com
127.0.0.1  spywarestrike.com #[Rogue/Suspect]
127.0.0.1  img.spywarestrike.com
127.0.0.1  sqcontrol.biz
127.0.0.1  yourguardonline.biz #[TR/Zlob.65745.8]
127.0.0.1  www.yourguardonline.biz
127.0.0.1  worldsecurityonline.biz #[TR/Dldr.Zlob.JX.2]
127.0.0.1  www.worldsecurityonline.biz
# [U-12 Group via Kevin Gerad][SafeSurf LLC]
127.0.0.1  spywarequake.com #[McAfee.SpywareQuake]
127.0.0.1  www.spywarequake.com #[Trojan.Fakealert]
127.0.0.1  download.spywarequake.com
127.0.0.1  www.spywarequake.info
127.0.0.1  urgentwindowsupdate.biz #[W32/Spywad.LO]
127.0.0.1  www.urgentwindowsupdate.biz
# [U-12 Group via Burst Technology GesmbH]
127.0.0.1  virusburst.com #[Sophos.VirusBurst]
127.0.0.1  dl3.virusburst.com
127.0.0.1  dl7.virusburst.com
127.0.0.1  dl8.virusburst.com
127.0.0.1  dl9.virusburst.com
127.0.0.1  download2.virusburst.com
127.0.0.1  download3.virusburst.com
127.0.0.1  download4.virusburst.com
127.0.0.1  download5.virusburst.com
127.0.0.1  download7.virusburst.com
127.0.0.1  download8.virusburst.com
127.0.0.1  download9.virusburst.com
127.0.0.1  download10.virusburst.com
127.0.0.1  download11.virusburst.com
127.0.0.1  download12.virusburst.com
127.0.0.1  download13.virusburst.com
127.0.0.1  download15.virusburst.com
127.0.0.1  download16.virusburst.com
127.0.0.1  www.virusburst.com #[Symantec.VirusBurst]
127.0.0.1  virusbursters.com #[McAfee.Adware-VirusBurst]
127.0.0.1  dl1.virusbursters.com
127.0.0.1  dl2.virusbursters.com
127.0.0.1  dl3.virusbursters.com
127.0.0.1  dl7.virusbursters.com
127.0.0.1  dl8.virusbursters.com
127.0.0.1  dl9.virusbursters.com
127.0.0.1  download2.virusbursters.com
127.0.0.1  download3.virusbursters.com
127.0.0.1  download4.virusbursters.com
127.0.0.1  download5.virusbursters.com
127.0.0.1  download7.virusbursters.com
127.0.0.1  download8.virusbursters.com
127.0.0.1  download9.virusbursters.com
127.0.0.1  download10.virusbursters.com
127.0.0.1  download11.virusbursters.com
127.0.0.1  download12.virusbursters.com
127.0.0.1  download13.virusbursters.com
127.0.0.1  download15.virusbursters.com
127.0.0.1  download16.virusbursters.com
127.0.0.1  www.virusbursters.com
# [U-12 Group via Privacyprotect.org]
127.0.0.1  expertantivirus.com #[WildCard DNS]
127.0.0.1  dl3.expertantivirus.com
127.0.0.1  www.expertantivirus.com #[Symantec.ExpertAntiVirus]
127.0.0.1  spylocked.com
127.0.0.1  dl2.spylocked.com
127.0.0.1  dl3.spylocked.com
127.0.0.1  dl5.spylocked.com
127.0.0.1  dl7.spylocked.com
127.0.0.1  dl8.spylocked.com
127.0.0.1  dl9.spylocked.com
127.0.0.1  download2.spylocked.com
127.0.0.1  download3.spylocked.com #[Win32/Adware.SpyLocked]
127.0.0.1  download4.spylocked.com
127.0.0.1  download5.spylocked.com
127.0.0.1  download7.spylocked.com
127.0.0.1  download8.spylocked.com
127.0.0.1  download9.spylocked.com
127.0.0.1  download10.spylocked.com
127.0.0.1  download11.spylocked.com
127.0.0.1  www.spylocked.com #[Symantec.SpyLocked]
127.0.0.1  virusprotectpro.com #[Trojan-Downloader.Win32.Zlob.bwe]
127.0.0.1  dl1.virusprotectpro.com
127.0.0.1  www.virusprotectpro.com #[Symantec.VirusProtectPro]
127.0.0.1  wildgadgets.biz
# [U-12 Group via Robyn Turner]
127.0.0.1  spydawn.com #[McAfee.SpyDawn]
127.0.0.1  dl1.spydawn.com #[Win32/Adware.SpywareQuake]
127.0.0.1  dl2.spydawn.com
127.0.0.1  dl3.spydawn.com
127.0.0.1  download2.spydawn.com #[Symantec.SpyDawn]
127.0.0.1  download3.spydawn.com
127.0.0.1  download4.spydawn.com
127.0.0.1  download5.spydawn.com
127.0.0.1  download7.spydawn.com
127.0.0.1  download8.spydawn.com
127.0.0.1  download9.spydawn.com
127.0.0.1  download10.spydawn.com
127.0.0.1  download11.spydawn.com
127.0.0.1  download12.spydawn.com
127.0.0.1  download13.spydawn.com
127.0.0.1  download15.spydawn.com
127.0.0.1  download16.spydawn.com
127.0.0.1  www.spydawn.com
# [End of Rogue/Suspect]
#
# [Rabbit Marketing Services]
127.0.0.1  netword.com #[Adware.Netword]
127.0.0.1  qry.netword.com
127.0.0.1  reg.netword.com
127.0.0.1  www.netword.com
127.0.0.1  www.rabbitmarketing.com #[ADW_NETWORD.A]
# [RevenueScience]
127.0.0.1  ads.revsci.net #[Ad-Aware Tracking.Cookie]
127.0.0.1  js.revsci.net
127.0.0.1  jsl.revsci.net
127.0.0.1  pix01.revsci.net #[TrackingPixelCode]
127.0.0.1  pix02.revsci.net
127.0.0.1  pix03.revsci.net
127.0.0.1  pix04.revsci.net
127.0.0.1  p.reuters.com #[gbl03.lb-revsci.net]
127.0.0.1  p.reuters.co.uk #[gbl19.lb-revsci.net]
127.0.0.1  rsi.buffalonews.com #[gbl33.lb-revsci.net]
127.0.0.1  rsi.nasdaq.com
127.0.0.1  rsi.thestreet.com #[gbl17.lb-revsci.net]
127.0.0.1  rsi.washingtonpost.com #[gbl25.lb-revsci.net]
127.0.0.1  rsi.webmd.com
127.0.0.1  p.wsj.com #[cust-gbl01.pix.revenuescience.net]
# [Round Up 4 Network][Tracking Service]
127.0.0.1  http100.content.ru4.com
127.0.0.1  http300.content.ru4.com
127.0.0.1  http.content.ru4.com #[pd.mii.instacontent.net]
127.0.0.1  http.edge.ru4.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  http1.edge.ru4.com
127.0.0.1  http2.edge.ru4.com
127.0.0.1  http3.edge.ru4.com #[Ewido.TrackingCookie.Ru4]
127.0.0.1  http4.edge.ru4.com
127.0.0.1  http5.edge.ru4.com #[McAfee.Cookie-RU4]
127.0.0.1  http6.edge.ru4.com
127.0.0.1  http7.edge.ru4.com
127.0.0.1  http8.edge.ru4.com #[SpySweeper.Spy.Cookie]
127.0.0.1  http9.edge.ru4.com
127.0.0.1  http10.edge.ru4.com #[SunBelt.Ru4.com]
127.0.0.1  http201.edge.ru4.com
127.0.0.1  http300.edge.ru4.com #[Accuserve Ad System]
127.0.0.1  http303.edge.ru4.com #[Tenebril.Tracking.Cookie]
127.0.0.1  https.edge.ru4.com #[pd.mirror-image.net]
127.0.0.1  http400.edge.ru4.com #[pd.mirror-image.net]
127.0.0.1  http-2081.edge.ru4.com
127.0.0.1  vpdc.ru4.com
# [Ruboskizo SL]
127.0.0.1  www.adbars.com #[SunBelt.AdBars]
127.0.0.1  www.bajasexo.com
127.0.0.1  alt.impresionesweb.com
127.0.0.1  www.impresionesweb.com
127.0.0.1  alternativos.iw-advertising.com
127.0.0.1  www.turbonic.com #[Adware.AdBars]
# [Rydium Canada/PCSTATS.COM]
127.0.0.1  ad-flow.com #[Tenebril.Tracking.Cookie]
127.0.0.1  ads.contextclick.com
127.0.0.1  impact.contextclick.com
127.0.0.1  www.techlinks100.com
# [Sedo LLC Group][Parking Service]
127.0.0.1  www.adsedo.com
127.0.0.1  sedoparking.com
127.0.0.1  img.sedoparking.com
127.0.0.1  www.sedoparking.com #[Microsoft.Typo-Patrol]
127.0.0.1  www1.sedoparking.com
127.0.0.1  www.sedotracker.com
127.0.0.1  www.sedotracker.de
# [Seed Corn Advertising Group]
127.0.0.1  happytofind.com #[Trojan-Dropper.Win32.Agent.hl]
127.0.0.1  download.happytofind.com
127.0.0.1  search.happytofind.com
127.0.0.1  www.happytofind.com #[Win32/TrojanClicker.IntelliAdvert]
127.0.0.1  topinstalls.com #[AVG.Trojan.Dropper.Agent.PP]
127.0.0.1  affiliates.topinstalls.com #[Win32/Adware.BookedSpace]
127.0.0.1  www.affiliates.topinstalls.com
127.0.0.1  software.topinstalls.com
127.0.0.1  www.topinstalls.com #[TROJ_SMALL.AAL][Adware.Links]
127.0.0.1  www.seedcornadvertising.com
127.0.0.1  www.seedcornadv.com
# [Seevast][Moniker][Kanoodle]
127.0.0.1  pops.404search.com #[McAfee.Adware-404Search]
127.0.0.1  secure.404search.com #[Adware-404Search][ADW_404SEARCH.A]
127.0.0.1  www.404search.com #[Sophos.404Search]
127.0.0.1  c2.edapebaf.com
127.0.0.1  click3.ekahfmal.com
127.0.0.1  app1.jkahfmal.com #[McAfee.Adware-SurfSideKick.dr]
127.0.0.1  app2.jkahfmal.com
127.0.0.1  banners.kanoodle.com
127.0.0.1  bt1.kanoodle.com
127.0.0.1  clickthrough.kanoodle.com
127.0.0.1  context1.kanoodle.com
127.0.0.1  context2.kanoodle.com
127.0.0.1  context3.kanoodle.com
127.0.0.1  context4.kanoodle.com
127.0.0.1  context5.kanoodle.com
127.0.0.1  safe.kanoodle.com
127.0.0.1  webmail.kanoodle.com
127.0.0.1  www.kanoodle.com #[SiteAdvisor.kanoodle.com]
127.0.0.1  search.trafficclub.com #[Microsoft.Typo-Patrol]
# [Seringhost Company][Wildcard DNS]
127.0.0.1  w.hqwmdjejtudlk-dfjkeid.com #[Trojan-Downloader.Win32.Rotarran.a]
127.0.0.1  up2.kjdhendieldiouyu.com #[virgins.se]
127.0.0.1  www.kjdhendieldiouyu.com #[McAfee.Adware-SafeSearch]
# [Server Central Network]
127.0.0.1  404ads.net
127.0.0.1  www.404ads.net
127.0.0.1  www.adconduit.net
127.0.0.1  tag2b.ads55.com
127.0.0.1  www.ads55.com
127.0.0.1  fcds.affiliatetracking.net
127.0.0.1  our.affiliatetracking.net
127.0.0.1  www.affiliatetracking.net
127.0.0.1  www.affiliatetracking.com
127.0.0.1  bookedspace.com
127.0.0.1  www.bookedspace.com #[Adware.Bookedspace]
127.0.0.1  download.centralserver.net #[McAfee.Adware-BkdSpace]
127.0.0.1  playteen.centralserver.net
127.0.0.1  www.keywordbarn.com
127.0.0.1  www.mixmaxmedia.com
127.0.0.1  searchclickads.net #[McAfee.Adware-BkdSpace.dr]
127.0.0.1  www.searchclickads.net
127.0.0.1  searchfu.net #[eTrust.SearchFu/123Search]
127.0.0.1  www.sparxads.com
127.0.0.1  wetrack.it
127.0.0.1  st.wetrack.it #[SunBelt.Wetrack.it]
127.0.0.1  www.zappbrannigan.com
127.0.0.1  www.zoombar.net #[SunBelt.ZoomBar]
# [Sessosubito.net Group]
127.0.0.1  www.baciamistupido.biz #[Dialer.BaciamiStupido][server down?]
127.0.0.1  www.coppiettaveneta.com #[zangocash.com]
127.0.0.1  www.defaultbar.com #[AdWare.Win32.Softomate.e]
127.0.0.1  www.doggyshock.com
127.0.0.1  qoogler.com #[Downloader.Goobiz]
127.0.0.1  www.qoogler.com
127.0.0.1  www.pelovero.com #[Trojan-Clicker.Win32.Small.hj]
127.0.0.1  www.popup-freesex-adv.biz #[Dialer.BaciamiStupido][server down?]
127.0.0.1  www.ricercadoppia.com #[AdWare.Win32.SideSearch.g]
127.0.0.1  www.super-videochat-community.biz #[Trojan.TrustedZone][server down?]
# [Shelron Group]
127.0.0.1  bestoffers.activeshopper.com
127.0.0.1  data2.activshopper.com #[Trackware.ActivShopper]
127.0.0.1  e-zshopper.activeshopper.com #[McAfee.Adware-ActivShop]
127.0.0.1  mini.activeshopper.com
127.0.0.1  mobile.activeshopper.com
127.0.0.1  search.activshopper.com
127.0.0.1  uk.activeshopper.com
127.0.0.1  www.shelrongroup.com
# [SJB Enterprises Inc]
127.0.0.1  www.bushleaguegame.com
127.0.0.1  www.mynetcompanion.com
127.0.0.1  mynetprotector.com #[Adware Bundler]
127.0.0.1  www.mynetprotector.com #[Rogue/Suspect]
127.0.0.1  www.mynetprotector.net #[SunBelt.MyNetProtector]
127.0.0.1  www.myspyprotector.com #[Rogue/Suspect]
127.0.0.1  www.netshagg.com #[SiteAdvisor.NetShagg]
127.0.0.1  www.sjbcorp.com
# [SiteMeter Inc][Tracking Service]
127.0.0.1  sitemeter.com #[SecuritySpace.WebBug]
127.0.0.1  ads.sitemeter.com
127.0.0.1  sm1.sitemeter.com
127.0.0.1  sm2.sitemeter.com #[SiteAdvisor.trustyhound.net]
127.0.0.1  sm3.sitemeter.com
127.0.0.1  sm4.sitemeter.com
127.0.0.1  sm5.sitemeter.com
127.0.0.1  sm6.sitemeter.com
127.0.0.1  sm7.sitemeter.com
127.0.0.1  sm8.sitemeter.com
127.0.0.1  sm9.sitemeter.com
127.0.0.1  s10.sitemeter.com
127.0.0.1  s11.sitemeter.com
127.0.0.1  s12.sitemeter.com
127.0.0.1  s13.sitemeter.com
127.0.0.1  s14.sitemeter.com
127.0.0.1  s15.sitemeter.com
127.0.0.1  s16.sitemeter.com
127.0.0.1  s17.sitemeter.com
127.0.0.1  s18.sitemeter.com
127.0.0.1  s19.sitemeter.com
127.0.0.1  s20.sitemeter.com
127.0.0.1  s21.sitemeter.com
127.0.0.1  s22.sitemeter.com
127.0.0.1  s23.sitemeter.com
127.0.0.1  s24.sitemeter.com
127.0.0.1  s25.sitemeter.com
127.0.0.1  s26.sitemeter.com
127.0.0.1  s27.sitemeter.com
127.0.0.1  s28.sitemeter.com
127.0.0.1  s29.sitemeter.com
127.0.0.1  s30.sitemeter.com
127.0.0.1  s31.sitemeter.com
127.0.0.1  s32.sitemeter.com
127.0.0.1  s33.sitemeter.com
127.0.0.1  s34.sitemeter.com
127.0.0.1  s35.sitemeter.com
127.0.0.1  s36.sitemeter.com
127.0.0.1  s37.sitemeter.com
127.0.0.1  s38.sitemeter.com
127.0.0.1  s39.sitemeter.com
127.0.0.1  s40.sitemeter.com
127.0.0.1  www.sitemeter.com
# [Sharman License Holdings][Adware Bundler]
127.0.0.1  kazaa.com
127.0.0.1  desktop.kazaa.com #[Tenebril.Tracking.Cookie]
127.0.0.1  download.kazaa.com
127.0.0.1  images.kazaa.com
127.0.0.1  www.kazaa.com
127.0.0.1  kazaa.adserver.co.il
127.0.0.1  www.kazaa.net.cn #[AdInstaller Control]
# [Sherv Inc][SiteAdvisor.sherv.net]
127.0.0.1  www.messengertools.net #[DrWeb.Tool.MsnSteal]
127.0.0.1  www.sherv.net #[AdWare.Win32.180Solutions][Adware-Sherv]
# [Shiny S.r.l]
127.0.0.1  codice.shinystat.com
127.0.0.1  codiceisp.shinystat.com
127.0.0.1  s1.shinystat.com
127.0.0.1  s2.shinystat.com
127.0.0.1  s3.shinystat.com
127.0.0.1  s4.shinystat.com
127.0.0.1  www.shinystat.com
127.0.0.1  codice.shinystat.it
127.0.0.1  codiceisp.shinystat.it
127.0.0.1  s1.shinystat.it
127.0.0.1  s2.shinystat.it #[SecuritySpace.WebBug]
127.0.0.1  s3.shinystat.it
127.0.0.1  s4.shinystat.it
127.0.0.1  www.shinystat.it
# [ShopNav][Walnut Ventures][Mike Thompson]
127.0.0.1  2020search.com #[Trojan.Digits][Spyware.2020search]
127.0.0.1  ws1.2020search.com
127.0.0.1  www.2020search.com #[CWS.Googlems.2][CWS.Winres]
127.0.0.1  appswebservice.com
127.0.0.1  ws1.appswebservice.com
127.0.0.1  404.drsnsrch.com
127.0.0.1  dlkw.drsnsrch.com #[SpySweeper.Adware.drsnsrch]
127.0.0.1  kw.drsnsrch.com
127.0.0.1  ron.drsnsrch.com
127.0.0.1  search.drsnsrch.com
127.0.0.1  search2.drsnsrch.com
127.0.0.1  toolbar.drsnsrch.com
127.0.0.1  websearch.drsnsrch.com #[Spyware.Shopnav.dl]
127.0.0.1  welcome.drsnsrch.com
127.0.0.1  www.drsnsrch.com
127.0.0.1  redzip.com #[SunBelt.Adw.RedZip.Toolbar]
127.0.0.1  www.redzip.com
127.0.0.1  shopnav.com
127.0.0.1  apps.shopnav.com
127.0.0.1  search.shopnav.com #[Sypware.Shopnav]
127.0.0.1  search.dr.shopnav.com #[if.searchcentrix.com]
127.0.0.1  soda.shopnav.com
127.0.0.1  websearch.shopnav.com
127.0.0.1  www.shopnav.com
127.0.0.1  srng.net #[ADW_SHOPNAV.D][CWS.ShopNav.D]
127.0.0.1  pop.popuptoast.com #[Spyware.2020search]
127.0.0.1  apps.webservicehosts.com #[Parasite.ShopNav]
127.0.0.1  dr.webservicehosts.com #[offeroptimizer.com]
127.0.0.1  gsim.webservicehosts.com
127.0.0.1  sc.webservicehosts.com #[McAfee.Downloader-AFN]
127.0.0.1  sn.webservicehosts.com #[McAfee.Adware-ShopNav]
# [SkyLabs Corporation][New York Internet Media][DL Enterprises]
127.0.0.1  www.favicon.com
127.0.0.1  searchblaster.com #[WIPO.Staples]
127.0.0.1  www.searchblaster.com #[Typo squatter]
127.0.0.1  wazam.com
127.0.0.1  www.wazam.com #[SunBelt.Wazam]
# [Skyline Network Technologies]
127.0.0.1  adtegrity.spinbox.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ema.spinbox.net
127.0.0.1  ia.spinbox.net
127.0.0.1  netcomm.spinbox.net
127.0.0.1  spin.spinbox.net
127.0.0.1  vsii.spinbox.net #[SunBelt.SpinBox]
127.0.0.1  www.spinbox.net
# [Snoggles]
127.0.0.1  www.freshseek.com #[McAfee.Adware-CWS]
127.0.0.1  blue.sexer.com
127.0.0.1  hello.sexer.com
127.0.0.1  white.sexer.com
127.0.0.1  ramgo.com
127.0.0.1  www.ramgo.com #[Win32.Startpage.B]
127.0.0.1  www.venusseek.com
# [SoftBulldog][Ran Geva]
127.0.0.1  www.diyp2p.com
127.0.0.1  www.dustat.com
127.0.0.1  www.gevamobile.com
127.0.0.1  www.malwhere.com
127.0.0.1  www.processid.com
127.0.0.1  www.rangeva.com
127.0.0.1  www.sigster.com
127.0.0.1  www.softbulldog.com #[Adware.MediaInject]
127.0.0.1  urlblaze.com #[Adware.IEDriver]
127.0.0.1  www.urlblaze.com #[SunBelt.UrlBlaze]
127.0.0.1  www.yadaware.com
# [Software, AdF]
127.0.0.1  www.downloadfree-games.com
127.0.0.1  www.downloadfreesoftware.net #[Adware.NewDotNet.B.Dropper]
127.0.0.1  www.download-free-screensavers.com
127.0.0.1  www.freecomputer-games.com
127.0.0.1  www.free-games-screensavers-wallpaper.com
127.0.0.1  www.free-games.to
127.0.0.1  www.freepc-games.com
127.0.0.1  www.freewallpaperbackgrounds.com #[AdWare.Win32.SaveNow.bo]
127.0.0.1  www.free-windows-games.com #[prompt.zangocash.com]
127.0.0.1  www.mp3musicsearch.net #[Server-Proxy.Win32.MarketScore.k]
127.0.0.1  www.safedownloads.net #[Adware Bundler]
# [Software Delivery Systems][BPS][HOHOST.COM][H4Host.com]
127.0.0.1  www.adnuker.com
127.0.0.1  www.adstriker.com
127.0.0.1  adwarecops.com #[Rogue/Suspect]
127.0.0.1  www.adwarecops.com
127.0.0.1  www.adwarestriker.com #[Rogue/Suspect]
127.0.0.1  antispyware.bulletproofsoft.com #[SiteAdvisor.bulletproofsoft.com]
127.0.0.1  download.bulletproofsoft.com
127.0.0.1  software.bulletproofsoft.com
127.0.0.1  spywareremoval.bulletproofsoft.com
127.0.0.1  www.bulletproofsoft.com #[Rogue/Suspect]
127.0.0.1  www.bulletproofsoft.net
127.0.0.1  www.cleanbrowser.com
127.0.0.1  www.downloadupload.com
127.0.0.1  www.filehog.com
127.0.0.1  www.spywarecops.com #[Rogue/Suspect]
127.0.0.1  www.spystriker.com #[Rogue/Suspect]
127.0.0.1  www.spywarestriker.com
127.0.0.1  www.spywarezapper.com #[Rogue/Suspect]
# [SourceForge]
127.0.0.1  ads.osdn.com
127.0.0.1  sfads.osdn.com
127.0.0.1  images-aud-pg.osdn.com
127.0.0.1  tg-images.osdn.com
127.0.0.1  images-aud.freshmeat.net
127.0.0.1  images-aud.slashdot.org
127.0.0.1  images-aud.sourceforge.net
# [Sparklit Networks]
127.0.0.1  imgserv.adbutler.com #[eTrust.Tracking.Cookie]
127.0.0.1  servedbyadbutler.com
127.0.0.1  adrotator.com
127.0.0.1  www.adrotator.com
127.0.0.1  counter.sparklit.com
127.0.0.1  vote.sparklit.com
127.0.0.1  webpoll.sparklit.com
# [SpecificMEDIA, Inc][ValueAd Inc]
127.0.0.1  www.gogotools.com #[Adware.GoGoTools]
127.0.0.1  www.searchgogo.com
127.0.0.1  specificpop.com #[SunBelt.Specificpop.com]
127.0.0.1  www.specificpop.com #[SpySweeper.Spy.Cookie]
127.0.0.1  specificclick.net
127.0.0.1  adopt.specificclick.net #[Ad-Aware.Tracking.Cookie]
127.0.0.1  afe.specificclick.net
127.0.0.1  dg.specificclick.net
127.0.0.1  images.specificclick.net
127.0.0.1  specificmedia.com
127.0.0.1  as.specificmedia.com #[usbansrv60]
127.0.0.1  cxtad.specificmedia.com
127.0.0.1  leads.specificmedia.com #[directtrack.com]
127.0.0.1  www.specificmedia.com #[eTrust.GoGoTools]
127.0.0.1  ac2.valuead.com
127.0.0.1  ads.valuead.com #[SpySweeper.Spy.Cookie]
127.0.0.1  adsignal.valuead.com
127.0.0.1  banners.valuead.com #[ADW_VALUEAD.M][eTrust.Tracking.Cookie]
127.0.0.1  oin.valuead.com #[outerinfo.com]
127.0.0.1  pmads.valuead.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  redux.valuead.com
127.0.0.1  reduxads.valuead.com #[Ewido.TrackingCookie.Valuead]
127.0.0.1  videodetectivenetwork.valuead.com
127.0.0.1  vdn.valuead.com
# [Speedbit Ltd][Feigenbaum, Idan]
127.0.0.1  ads.downloadaccelerator.com
127.0.0.1  ad1.speedbit.com
127.0.0.1  ad2.speedbit.com
127.0.0.1  ad3.speedbit.com
127.0.0.1  ad4.speedbit.com
127.0.0.1  ad5.speedbit.com
127.0.0.1  ad6.speedbit.com
127.0.0.1  ad7.speedbit.com
127.0.0.1  ad8.speedbit.com
127.0.0.1  ad9.speedbit.com
127.0.0.1  ad10.speedbit.com
127.0.0.1  ads1.speedbit.com
127.0.0.1  ads2.speedbit.com
127.0.0.1  ads3.speedbit.com
127.0.0.1  ads4.speedbit.com
127.0.0.1  ads5.speedbit.com
127.0.0.1  ads6.speedbit.com
127.0.0.1  ads7.speedbit.com
127.0.0.1  ads8.speedbit.com
127.0.0.1  ads9.speedbit.com
127.0.0.1  ads10.speedbit.com
127.0.0.1  mirrorsearch.speedbit.com
# [Speedera Networks][Akamai Technologies][VPP Technologies]
127.0.0.1  adt.m7z.net #[a1827.x.akamai.net]
127.0.0.1  bridgetrack.speedera.r3h.net
127.0.0.1  anon.doubleclick.speedera.net
127.0.0.1  spd.atdmt.speedera.net
127.0.0.1  falk.speedera.net
127.0.0.1  fms2.pointroll.speedera.net
127.0.0.1  tribalfusion.speedera.net #[a889.g.akamai.net]
127.0.0.1  app.whenu.speedera.net
127.0.0.1  weather.whenu.speedera.net
127.0.0.1  web.whenu.speedera.net #[a1401.x.akamai.net]
127.0.0.1  agentq.vpptechnologies.com
127.0.0.1  js.vpptechnologies.com
127.0.0.1  media-0.vpptechnologies.com
127.0.0.1  media-1.vpptechnologies.com
127.0.0.1  media-2.vpptechnologies.com #[SiteAdvisor.fish-screensaver.com]
127.0.0.1  media-4.vpptechnologies.com
127.0.0.1  media-5.vpptechnologies.com
127.0.0.1  media-6.vpptechnologies.com
127.0.0.1  media-8.vpptechnologies.com #[SiteAdvisor.fish-screensaver.com]
127.0.0.1  media-a.vpptechnologies.com #[a599.x.akamai.net]
127.0.0.1  media-b.vpptechnologies.com
127.0.0.1  media-c.vpptechnologies.com #[a1332.x.akamai.net]
127.0.0.1  media-d.vpptechnologies.com
127.0.0.1  media-e.vpptechnologies.com
127.0.0.1  media-f.vpptechnologies.com
127.0.0.1  msxml.vpptechnologies.com
127.0.0.1  static.vpptechnologies.com #[hotsearchbar.com]
127.0.0.1  xml.vpptechnologies.com #[BlazeFind]
# [Spylog][MyWebProjects]
127.0.0.1  spytrack.tic.ru
127.0.0.1  spylog.com #[SecuritySpace.WebBug]
127.0.0.1  banners.spylog.com
127.0.0.1  gstats.spylog.com #[Tenebril.Tracking.Cookie]
127.0.0.1  hits.spylog.com #[SunBelt.SpyLog.com]
127.0.0.1  my.spylog.com
127.0.0.1  stats.spylog.com
127.0.0.1  www.spylog.com
127.0.0.1  spylog.ru
127.0.0.1  dir.spylog.ru
127.0.0.1  dir1.spylog.ru
127.0.0.1  gs.spylog.ru
127.0.0.1  info.spylog.ru
127.0.0.1  tools.spylog.ru
127.0.0.1  www.spylog.ru
127.0.0.1  adv.aport.ru
127.0.0.1  counter.aport.ru
# [Spyware Labs, Inc][Adware.AdDestroyer]
127.0.0.1  spywarelabs.com #[Adware.VirtualBouncer]
127.0.0.1  download.spywarelabs.com #[ADW_ADDESTROY.A]
127.0.0.1  install.spywarelabs.com #[ADW_BUNDOUT.A]
127.0.0.1  spywarelabs.fileburst.com
127.0.0.1  xml.spywarelabs.com
127.0.0.1  www.spywarelabs.com #[Rogue/Suspect]
127.0.0.1  virtualbouncer.com #[SPYW_VBOUNCE.B]
127.0.0.1  www.virtualbouncer.com #[Rogue/Suspect]
# [SRC Technologies]
127.0.0.1  lsjmp.com
127.0.0.1  www.postalmanager.com
127.0.0.1  spybouncer.com #[Rogue/Suspect]
127.0.0.1  spywareremover.spybouncer.com
127.0.0.1  www.spybouncer.com #[SpyBouncer.SBDownloader]
# [STANDARD INTERNET / Datapipe Group][Adware.Winpup]
127.0.0.1  adserv.net
127.0.0.1  adtrak.net #[SunBelt.Adtrak.net]
127.0.0.1  ugl.adtrak.net
127.0.0.1  www.adtrak.net
127.0.0.1  www.claxon.com
127.0.0.1  claxonmedia.com
127.0.0.1  www.claxonmedia.com
127.0.0.1  popuptraffic.com #[Parasite.ClientMan]
127.0.0.1  media.popuptraffic.com #[Tenebril.Tracking.Cookie]
127.0.0.1  media2.popuptraffic.com
127.0.0.1  stats.popuptraffic.com #[SunBelt.PopupTraffic.com]
127.0.0.1  www.popuptraffic.com
127.0.0.1  sictalk.com
127.0.0.1  www.standardinternet.com #[SunBelt.StandardInternet]
# [StartNow International][eTrust.StartNow.HyperBar]
127.0.0.1  www.goodsitesguide.com
127.0.0.1  adserver.startnow.com
127.0.0.1  go.startnow.com
127.0.0.1  minisearch.startnow.com #[Adware.IESearch]
127.0.0.1  nav.startnow.com #[W32.Anpes@mm]
127.0.0.1  search.startnow.com
127.0.0.1  srch.startnow.com
127.0.0.1  toolbar.startnow.com #[SunBelt.StartNow Hyperbar]
127.0.0.1  www.startnow.com #[Adware.HyperBar]
127.0.0.1  www.webtracknow.com
127.0.0.1  download.wyzo.com
127.0.0.1  start.wyzo.com
127.0.0.1  www.wyzo.com
# [Statcounter][Aodhan Cullen]
127.0.0.1  c1.statcounter.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  c2.statcounter.com #[SecuritySpace.WebBug]
127.0.0.1  c3.statcounter.com #[eTrust.Tracking.Cookie]
127.0.0.1  c4.statcounter.com
127.0.0.1  c5.statcounter.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c6.statcounter.com #[MVPS.Criteria]
127.0.0.1  c7.statcounter.com
127.0.0.1  c8.statcounter.com #[McAfee.Cookie-Statcounter]
127.0.0.1  c10.statcounter.com
127.0.0.1  c11.statcounter.com #[Ewido.TrackingCookie.Statcounter]
127.0.0.1  c12.statcounter.com
127.0.0.1  c13.statcounter.com
127.0.0.1  c14.statcounter.com
127.0.0.1  c15.statcounter.com
127.0.0.1  c16.statcounter.com
127.0.0.1  c17.statcounter.com
127.0.0.1  c18.statcounter.com
127.0.0.1  c19.statcounter.com
127.0.0.1  my.statcounter.com
127.0.0.1  s2.statcounter.com #[SunBelt.statcounter.com]
127.0.0.1  secure.statcounter.com
127.0.0.1  www.statcounter.com
# [STATSnet]
127.0.0.1  counted.com
127.0.0.1  bilbo.counted.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.counted.com
127.0.0.1  www.stats.net
# [Steve Banton]
127.0.0.1  allstargaming.net #[ADW_SPEYLOD.D]
127.0.0.1  www.allstargaming.net
127.0.0.1  electricroms.com
127.0.0.1  www.electricroms.com
127.0.0.1  www.sexyfreescreensavers.com #[AdWare.Win32.Softomate.ah]
# [Steve Velikog]
127.0.0.1  srv01.bashchelik.com #[Trojan.Mancsyn]
127.0.0.1  mildred.debelizombi.com
127.0.0.1  srv01.debelizombi.com
# [Sticky Logic]
127.0.0.1  www.stickylogic.com
127.0.0.1  www.winadiscount.com #[Dr.Web.Adware.Xbarre]
127.0.0.1  www.winaproduct.com
# [Strive Investments AVV]
127.0.0.1  www.privacychampion.com #[Rogue/Suspect]
# [SubscriberBASE Inc]
127.0.0.1  www.addrive.com
127.0.0.1  bluezipper.com #[eTrust.PrecisionPop]
127.0.0.1  hpu.bluezipper.com
127.0.0.1  www.bluezipper.com
127.0.0.1  exceip.com #[Whois.Blacklisted]
127.0.0.1  www.freeslide.com
127.0.0.1  jdaf.com
127.0.0.1  jp1.sb01.com #[SpySweeper.Spy.Cookie]
127.0.0.1  sbase30.com
127.0.0.1  mx253.sb03.com #[HJTH.FavoriteMan]
127.0.0.1  precisionpop.com
127.0.0.1  adserve.precisionpop.com
127.0.0.1  context.precisionpop.com
127.0.0.1  www.precisionpop.com #[Adware.PrecisionPop]
127.0.0.1  subscriberbase.com
127.0.0.1  www.weeklysurveys.com
# [SwankSoft][Danilo Ladendorf][FTC Action]
127.0.0.1  www.anthraxalarm.com
127.0.0.1  www.historykill.com
127.0.0.1  www.killercash.com
127.0.0.1  www.spykiller.com #[Rogue/Suspect]
127.0.0.1  www.surfmask.com
127.0.0.1  www.swanksoft.com
127.0.0.1  www.trustsoft.com
127.0.0.1  www.winprivacy.com
# [System Initial]
127.0.0.1  www.foxik.com #[MHTMLRedir.Exploit]
127.0.0.1  www.ruworld.com #[MHTMLRedir.Exploit]
127.0.0.1  sysini.com
127.0.0.1  www.sysini.com
127.0.0.1  turboinet.com
127.0.0.1  www.turboinet.com
# [T2 Technologies Group]
127.0.0.1  ad.t2t2.com
127.0.0.1  bookmark.t2t2.com
127.0.0.1  iebar.t2t2.com #[Adware.Iebar]
127.0.0.1  jump.t2t2.com #[AdWare.ToolBar.Iebar.c]
127.0.0.1  stat.t2t2.com
127.0.0.1  vip2.t2t2.com
127.0.0.1  vip6.t2t2.com
127.0.0.1  www.t2t2.com
127.0.0.1  stat1.vipstat.com
# [Tacoda Systems]
127.0.0.1  te.audiencematch.net #[McAfee.Cookie-Audiencematch]
127.0.0.1  an.tacoda.net #[a1406.g.akamai.net]
127.0.0.1  anad.tacoda.net #[BurstMedia]
127.0.0.1  anat.tacoda.net
127.0.0.1  anrtx.tacoda.net
127.0.0.1  te.tacoda.net #[Ewido.TrackingCookie.Tacoda]
127.0.0.1  tribune.tacoda.net
# [TAM Network]
127.0.0.1  adimgs.com
127.0.0.1  c.adverpages.com
127.0.0.1  c.mydirectweb.com #[ofrsvr.com]
127.0.0.1  i.mydirectweb.com #[adimgs.com]
127.0.0.1  www.rxwebsearch.com
127.0.0.1  c.thinktarget.com #[Parked?]
127.0.0.1  farm.thinktarget.com
127.0.0.1  g.thinktarget.com
127.0.0.1  search.thinktarget.com
127.0.0.1  secretmaker.thinktarget.com #[farm.thinktarget.com]
# [TargetSaver, Inc]
127.0.0.1  www.adtraffic.net #[eTrust.Adtraffic]
127.0.0.1  www.quicksweeper.com
127.0.0.1  targetsaver.com #[SpySweeper.Adware.targetsaver]
127.0.0.1  a.targetsaver.com
127.0.0.1  dl.targetsaver.com #[ADW_TARGETSAV.A]
127.0.0.1  www.targetsaver.com #[Adware.TargetSaver]
127.0.0.1  www.targetweather.com
# [Telecom Tech Group]
127.0.0.1  www.firstgoodsearch.com #[TR/Dldr.YM]
127.0.0.1  www.numb-soft.com #[Trojan-Downloader.Win32.Agent.ahv]
# [Telemark Info-Media]
127.0.0.1  adx.hendersonvillenews.com
127.0.0.1  adx.heraldtribune.com #[nyads.ny.publicus.com]
127.0.0.1  adx.starbanner.com
127.0.0.1  adx.telegram.com
127.0.0.1  adx.theledger.com
127.0.0.1  haimg.no.publicus.com
127.0.0.1  noads.no.publicus.com
127.0.0.1  llimg.ny.publicus.com
127.0.0.1  srimg.ny.publicus.com
127.0.0.1  wtimg.ny.publicus.com
127.0.0.1  bbads.sv.publicus.com
127.0.0.1  bjimg.sv.publicus.com
127.0.0.1  cdimg.sv.publicus.com
127.0.0.1  cmads.sv.publicus.com
127.0.0.1  ctimg.sv.publicus.com
127.0.0.1  fdads.sv.publicus.com
127.0.0.1  nsads.sv.publicus.com
127.0.0.1  rhads.sv.publicus.com
127.0.0.1  vdimg.sv.publicus.com
127.0.0.1  geads.us.publicus.com
127.0.0.1  gr.us.publicus.com
127.0.0.1  lladinserts.us.publicus.com
# [TG Publishing AG]
127.0.0.1  www.ad.denguru.com
127.0.0.1  www.ad.mobilityguru.com
127.0.0.1  a.tomshardware.com #[ehg-tgpublishing.hitbox.com]
127.0.0.1  ad.tomshardware.com
127.0.0.1  www.ad.tomshardware.com
127.0.0.1  www.ad.twitchguru.com
#[The DelFin Project][Adware.DelFin][Adware.DelFin.B]
127.0.0.1  delfinproject.com #[ADW_DELFINMED.C]
127.0.0.1  ads.delfinproject.com
127.0.0.1  adsv2.delfinproject.com #[Softure AdServer]
127.0.0.1  content.delfinproject.com #[Adware-IEDriver]
127.0.0.1  mm.delfinproject.com #[AdWare.DelphinMediaViewer.c]
127.0.0.1  storagev2.delfinproject.com #[McAfee.Downloader-JS]
127.0.0.1  www.delfinproject.com #[Adware-PromulGate]
127.0.0.1  www.elottoalert.com
127.0.0.1  storage.savingshound.com
127.0.0.1  www.savingshound.com #[Adware.SavingsHound]
127.0.0.1  www.winfallpublishing.com
# [The Walt Disney Company][ABC News][INFOSEEK]
127.0.0.1  3ps.go.com
# 127.0.0.1  hb.disney.go.com #[disabled affects links]
127.0.0.1  ad.go.com
127.0.0.1  adimages.go.com
127.0.0.1  dcapps.disney.go.com #[web bug]
127.0.0.1  ehg-espn.hitbox.com #[SunBelt.Ehg-ESPN.Hitbox]
127.0.0.1  ngads.go.com
127.0.0.1  ad.infoseek.com
127.0.0.1  adsatt.abcnews.starwave.com
127.0.0.1  adsatt.disney.starwave.com
127.0.0.1  adsatt.espn.go.com
127.0.0.1  adsatt.espn.starwave.com
127.0.0.1  adsatt.familyfun.starwave.com
127.0.0.1  adsatt.go.starwave.com
127.0.0.1  adsatt.movies.starwave.com
127.0.0.1  odc.starwave.com
# [Think Partnership]
127.0.0.1  1.primaryads.com #[SpySweeper.Spy.Cookie][directtrack.com]
127.0.0.1  aff.primaryads.com #[MVPS.Criteria]
127.0.0.1  images.primaryads.com
# [Thruport Technologies]
127.0.0.1  fcc.adjuggler.com
127.0.0.1  image.adjuggler.com
127.0.0.1  img1.adjuggler.com
127.0.0.1  img2.adjuggler.com
127.0.0.1  imgall.adjuggler.com
127.0.0.1  image.dex.adjuggler.com
127.0.0.1  rotator.adjuggler.com
127.0.0.1  rotator.dex.adjuggler.com
127.0.0.1  rotator.its.adjuggler.com #[SiteAdvisor.myAdultExplorer.com]
127.0.0.1  thunderbolt.adjuggler.com
127.0.0.1  traffic.adjuggler.com #[eTrust.Tracking.Cookie]
127.0.0.1  www.adjuggler.com
127.0.0.1  adshttp.com
127.0.0.1  img1.adshttp.com
127.0.0.1  adsonwww.com
127.0.0.1  dnaads.com
127.0.0.1  empnads.com
127.0.0.1  gamesbanner.net
127.0.0.1  www.gamesbanner.net
127.0.0.1  ads.heraldnet.com #[rotator.adjuggler.com]
127.0.0.1  httpwwwads.com
127.0.0.1  ads.realtechnetwork.net
127.0.0.1  network.realtechnetwork.net
127.0.0.1  thruport.com
127.0.0.1  adj43.thruport.com
127.0.0.1  adj50.thruport.com
127.0.0.1  adj54.thruport.com
127.0.0.1  imageserver1.thruport.com
127.0.0.1  www.thruport.com
# [TopRebates, LLC][Tom Richmond]
127.0.0.1  www.e-traffic.com
127.0.0.1  www.etraffic.com
127.0.0.1  www.sysupdates.com
127.0.0.1  www.sysupdates2.com
127.0.0.1  topfivesearch.com #[TROJ_DLOADER.VR]
127.0.0.1  xml.topfivesearch.com #[VPP Technologies]
127.0.0.1  www.topfivesearch.com #[eTrust.TopFiveSearch]
127.0.0.1  topmoxie.com #[SunBelt.TopMoxie]
127.0.0.1  support.topmoxie.com
127.0.0.1  www.topmoxie.com #[Etraffic]
127.0.0.1  www.topmoxie2.com #[Adware.WebRebates.B]
127.0.0.1  toprebate.com
127.0.0.1  www.toprebate.com
127.0.0.1  toprebates.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.toprebates.com #[Adware.WebRebates]
# [Total Velocity][Adware.MemoryMeter]
127.0.0.1  memorymeter.com #[Adware-TVelocity][TotalVelocity.MemoryMeter]
127.0.0.1  www.memorymeter.com
127.0.0.1  totalvelocity.com #[TV T-Media Display]
127.0.0.1  www.totalvelocity.com
# [Trade Doubler AB]
127.0.0.1  tradedoubler.com #[eTrust.Tracking.Cookie]
127.0.0.1  clk.tradedoubler.com
127.0.0.1  clkde.tradedoubler.com #[McAfee.Adware-Littlehelper]
127.0.0.1  clkuk.tradedoubler.com
127.0.0.1  hstde.tradedoubler.com #[SunBelt.TradeDoubler.com]
127.0.0.1  hstes.tradedoubler.com
127.0.0.1  hstfr.tradedoubler.com
127.0.0.1  hstgb.tradedoubler.com
127.0.0.1  hstit.tradedoubler.com
127.0.0.1  hstno.tradedoubler.com #[Ewido.TrackingCookie.Tradedoubler]
127.0.0.1  hstpl.tradedoubler.com
127.0.0.1  hstus.tradedoubler.com
127.0.0.1  img.tradedoubler.com
127.0.0.1  impbe.tradedoubler.com #[Panda.Spyware:Cookie/Tradedoubler]
127.0.0.1  impch.tradedoubler.com
127.0.0.1  impde.tradedoubler.com
127.0.0.1  impdk.tradedoubler.com
127.0.0.1  impes.tradedoubler.com
127.0.0.1  impfi.tradedoubler.com
127.0.0.1  impfr.tradedoubler.com
127.0.0.1  impgb.tradedoubler.com #[SecuritySpace.WebBug]
127.0.0.1  impie.tradedoubler.com
127.0.0.1  impit.tradedoubler.com
127.0.0.1  implt.tradedoubler.com
127.0.0.1  impnl.tradedoubler.com
127.0.0.1  impno.tradedoubler.com
127.0.0.1  imppl.tradedoubler.com
127.0.0.1  impse.tradedoubler.com
127.0.0.1  pf.tradedoubler.com
127.0.0.1  tracker.tradedoubler.com #[McAfee.Cookie-Tradedoubler]
# [Trade News Corporation][Wildcard DNS]
127.0.0.1  www.1adult.com
127.0.0.1  11zz.com
127.0.0.1  i.11zz.com
127.0.0.1  in.11zz.com
127.0.0.1  www.11zz.com
127.0.0.1  adultlinksco.com
127.0.0.1  www.adultlinksco.com
127.0.0.1  cashcount.com
127.0.0.1  www.cashcount.com
127.0.0.1  cecash.com
127.0.0.1  image.cecash.com
127.0.0.1  tats.cecash.com
127.0.0.1  www.cecash.com
127.0.0.1  coolwebstats.com
127.0.0.1  www.coolwebstats.com
127.0.0.1  in.cybererotica.com
127.0.0.1  tats.cybererotica.com
127.0.0.1  tour.cybererotica.com
127.0.0.1  www.cybererotica.com
127.0.0.1  ezcybersearch.com #[EZCyberSearch.Surebar][Adware-EZSearch]
127.0.0.1  ads.ezcybersearch.com #[Adware.EZSearch.B]
127.0.0.1  www.ezcybersearch.com #[Parasite.ezCyberSearch]
127.0.0.1  in.ff5.com
127.0.0.1  in.joinourwebsite.com
127.0.0.1  www.joinourwebsite.com
127.0.0.1  mainentrypoint.com #[eTrust.AdultLinks.Qabar]
127.0.0.1  in.mainentrypoint.com #[SunBelt.MainEntryPoint]
127.0.0.1  lz.mainentrypoint.com
127.0.0.1  secure.mainentrypoint.com
127.0.0.1  vad.mainentrypoint.com
127.0.0.1  www.mainentrypoint.com #[Adware.AdultLinks]
127.0.0.1  tgp.pornsponsors.com
127.0.0.1  www.pornsponsors.com
127.0.0.1  in.riskymail4free.com #[Spamdexing]
127.0.0.1  www.riskymail4free.com
127.0.0.1  search-itnow.com #[Parasite.AdultLinks]
127.0.0.1  www.search-itnow.com #[McAfee.Adware-AdultLinks]
127.0.0.1  bigtits.xxxallaccesspass.com
# [Trafficaces]
127.0.0.1  680130.net #[ADW_DLOADER.NT]
127.0.0.1  adserv.680130.net
127.0.0.1  update.680130.net
127.0.0.1  www.680130.net
# [TrafficAds Media][Findology Interactive Media]
127.0.0.1  www.findology.com #[PCTools.ezSearching]
127.0.0.1  findology.mail.everyone.net
127.0.0.1  trafficads.com
127.0.0.1  www.trafficads.com
# [Traffix Inc]
127.0.0.1  adc.aavalue.com
127.0.0.1  adserv.aavalue.com
127.0.0.1  atlaseducation.aavalue.com
127.0.0.1  ezgreets.aavalue.com
127.0.0.1  eztracks.aavalue.com #[McAfee.Adware-EZTracks]
127.0.0.1  getmusicfree.aavalue.com
127.0.0.1  greatoffers.aavalue.com
127.0.0.1  grouplotto.aavalue.com
127.0.0.1  lottofanatic.aavalue.com
127.0.0.1  lovefreegames.aavalue.com #[Adware.LoveFreeGames]
127.0.0.1  mrsupergames.aavalue.com #[AdWare.Win32.Eztracks.a]
127.0.0.1  musicoffaith.aavalue.com #[NOD32.Win32/Adware.SideSearch]
127.0.0.1  prizeamerica.aavalue.com
127.0.0.1  reciperewards.aavalue.com #[AdWare.Win32.SideSearch.g]
127.0.0.1  thumbplay.aavalue.com
127.0.0.1  trynewgames.aavalue.com
127.0.0.1  watchfreeflix.aavalue.com
127.0.0.1  www.clearflow.com
127.0.0.1  www.clickhelp.net
127.0.0.1  ww1.ez-screensavers.com #[Trojan.BettInet.A]
127.0.0.1  www.ez-screensavers.com
127.0.0.1  freemusic.ez-tracks.com
127.0.0.1  ww2.ez-tracks.com
127.0.0.1  www.ez-tracks.com
127.0.0.1  gamefiesta.com
127.0.0.1  cardgames.gamefiesta.com
127.0.0.1  images.gamefiesta.com #[p.mii.instacontent.net]
127.0.0.1  search.gamefiesta.com
127.0.0.1  www.gamefiesta.com
127.0.0.1  cache.grouplotto.com
127.0.0.1  register7.grouplotto.com
127.0.0.1  www.grouplotto.com
127.0.0.1  images.infiads.com #[p.mii.instacontent.net]
127.0.0.1  www.infiads.com
127.0.0.1  www.lovefreegames.com #[Adware.LoveFreeGames]
127.0.0.1  search.mrsupergames.com
127.0.0.1  www.mrsupergames.com
127.0.0.1  www.mrsupergames-jump.com
127.0.0.1  tbdev.pickoftheweb.com
127.0.0.1  mailpop.pickoftheweb.com
127.0.0.1  toolbar.pickoftheweb.com #[Fun and Games Toolbar]
127.0.0.1  www.pickoftheweb.com #[Adware.EZToolbar]
127.0.0.1  ww1.reciperewards.com
127.0.0.1  searchinaflash.com
127.0.0.1  ezgreets.searchinaflash.com
127.0.0.1  eztracks.searchinaflash.com
127.0.0.1  www.searchinaflash.com
127.0.0.1  track.sendtraffic.com
127.0.0.1  www.sendtraffic.com
127.0.0.1  www.traffixinc.com #[SunBelt.Traffix]
127.0.0.1  jumps.watchfreeflix.com
# [TrekBlue][Trek Eight]
127.0.0.1  123.fluxads.com
127.0.0.1  www.spywarenuker.com #[Adware.SpywareNuker]
# [Tribal Fusion][Dilip DaSilva]
127.0.0.1  tags.expo9.exponential.com
127.0.0.1  tribalfusion.com #[eTrust.Tracking.Cookie]
127.0.0.1  a.tribalfusion.com
127.0.0.1  cdn1.tribalfusion.com #[SunBelt.TribalFusion][a889.g.akamai.net]
127.0.0.1  cdn4.tribalfusion.com #[Ewido.TrackingCookie.Tribalfusion]
127.0.0.1  cdn5.tribalfusion.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ctxt.tribalfusion.com
127.0.0.1  m.tribalfusion.com
127.0.0.1  s.tribalfusion.com
127.0.0.1  www.tribalfusion.com #[McAfee.Cookie-Tribalfusion]
# [Unicast Communications][Viewpoint]
127.0.0.1  creativeby1.unicast.com #[viewpointn.vo.llnwd.net]
127.0.0.1  ping1.unicast.com
127.0.0.1  www3.unicast.com
127.0.0.1  www.unicast.com #[SunBelt.Unicast]
# [USA Revco][PBH LLC]
127.0.0.1  r3.chkdat.com
127.0.0.1  r6.chksvc.com
127.0.0.1  r7.chksvc.com
127.0.0.1  clear-search.com
127.0.0.1  www.clear-search.com #[eTrust.Clear-Search]
127.0.0.1  clrsch.com #[Adware.ClearSearch]
127.0.0.1  r2.clrsch.com
127.0.0.1  r3.clrsch.com
127.0.0.1  r4.clrsch.com
127.0.0.1  sds.clrsch.com #[TROJ_SMALL.GO]
127.0.0.1  status.clrsch.com #[W32/ClearSearch.AI.dropper]
127.0.0.1  www.clrsch.com
127.0.0.1  s1.qckads.com
127.0.0.1  s2.qckads.com
127.0.0.1  s3.qckads.com
127.0.0.1  s4.qckads.com
127.0.0.1  s5.qckads.com
127.0.0.1  s6.qckads.com
127.0.0.1  s7.qckads.com
127.0.0.1  sds.qckads.com
127.0.0.1  status.qckads.com
127.0.0.1  r6.svcmgr.com
# [ValueClick Media]
127.0.0.1  www.afcyhf.com #[SecuritySpace.WebBug]
127.0.0.1  www.anrdoezrs.net
127.0.0.1  www.apmebf.com #[Panda.Spyware:Cookie/Apmebf][SpySweeper.Spy.Cookie]
127.0.0.1  www.awltovhc.com #[SecuritySpace.WebBug]
127.0.0.1  ads.bfast.com #[McAfee.Cookie-Bfast][SecuritySpace.WebBug]
127.0.0.1  service.bfast.com #[Ewido.TrackingCookie.Bfast]
127.0.0.1  service2.bfast.com #[Tenebril.Tracking.Cookie]
127.0.0.1  cj.com
127.0.0.1  www.cj.com #[SunBelt.WWW.CJ.com]
127.0.0.1  clickagents.com #[SunBelt.ClickAgents.com]
127.0.0.1  st.clickagents.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.clickagents.com #[eTrust.ClickAgents.com]
127.0.0.1  www.commission-junction.com #[eTrust.Tracking.Cookie]
127.0.0.1  www.dpbolvw.net
127.0.0.1  www.emjcd.com
127.0.0.1  www.ftjcfx.com #[SecuritySpace.WebBug]
127.0.0.1  www.jdoqocy.com
127.0.0.1  www.kqzyfj.com
127.0.0.1  www.lduhtrp.net #[SecuritySpace.WebBug]
127.0.0.1  mediaplex.com #[eTrust.Tracking.Cookie]
127.0.0.1  adfarm.mediaplex.com #[Adware.Meplex][Adware-DesktopMedia.dr]
127.0.0.1  ad.snv.mediaplex.com
127.0.0.1  altfarm.mediaplex.com #[may affect eBay][MVPS.Criteria]
127.0.0.1  img.mediaplex.com #[Ewido.TrackingCookie.Mediaplex]
127.0.0.1  img-cdn.mediaplex.com
127.0.0.1  img-snv.mediaplex.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.mediaplex.com #[SunBelt.Mediaplex.com]
127.0.0.1  qksrv.com
127.0.0.1  www.qksrv.net #[eTrust.Tracking.Cookie]
127.0.0.1  search123.com #[SunBelt.Search123.com]
127.0.0.1  click.search123.com
127.0.0.1  cgi.search123.com
127.0.0.1  partners.search123.com
127.0.0.1  www.search123.com #[SunBelt.SearchExe Hijacker]
127.0.0.1  www.qksz.net
127.0.0.1  www.tkqlhce.com
127.0.0.1  www.tqlkg.com #[SecuritySpace.WebBug]
127.0.0.1  valueclick.com #[eTrust.Tracking.Cookie][SunBelt.ValueClick.com]
127.0.0.1  st.valueclick.ne.jp
127.0.0.1  oz.valueclick.ne.jp
127.0.0.1  ads.bfm.valueclick.net
127.0.0.1  ads.blp.valueclick.net
127.0.0.1  ads.fhm.valueclick.net
127.0.0.1  ads.he.valueclick.net
127.0.0.1  ads.hnet.valueclick.net
127.0.0.1  ads.mplx.valueclick.net
127.0.0.1  ads.mtv.valueclick.net
127.0.0.1  ads.mv.valueclick.net
127.0.0.1  ads.npr.valueclick.net
127.0.0.1  ads.pr.valueclick.net
127.0.0.1  ads.scot.valueclick.net
127.0.0.1  ads.vcuk.valueclick.net
127.0.0.1  cdn.valueclick.net
127.0.0.1  images.valueclickmedia.com
127.0.0.1  ab.vcmedia.com
127.0.0.1  www.yceml.net
127.0.0.1  adfarm.mplx.akadns.net #[SiteAdvisor.livingwater4u.com]
127.0.0.1  img.mplx.akadns.net #[SiteAdvisor.aim.com]
# [ValueClick via Web Clients]
127.0.0.1  webclients.net #[Webclients Ad Network]
127.0.0.1  banners3.webclients.net
127.0.0.1  www.webclients.net
127.0.0.1  websponsors.com
127.0.0.1  a.websponsors.com #[SunBelt.a.websponsors]
127.0.0.1  ads.websponsors.com
127.0.0.1  g.websponsors.com #[Whois.Blacklisted]
127.0.0.1  ocs.websponsors.com
127.0.0.1  www.websponsors.com
# [ValueClick Media via FastClick][Tracking Service]
127.0.0.1  fastclick.com
127.0.0.1  www.fastclick.com #[SunBelt.FastClick.com]
127.0.0.1  cdn.fastclick.net
127.0.0.1  code.fastclick.net
127.0.0.1  images.fastclick.net #[Panda.Spyware:Cookie/FastClick]
127.0.0.1  media.fastclick.net
127.0.0.1  secure.fastclick.net #[Tenebril.Tracking.Cookie]
127.0.0.1  fastclick.com.edgesuite.net #[a1795.g.akamai.net]
# [Vendare Group][Navigation Catalyst Systems]
127.0.0.1  www.bestsearchonearth.info
127.0.0.1  info.browserdirect.net
127.0.0.1  casalamedia.com
127.0.0.1  www.casalamedia.com #[qsrch.com]
127.0.0.1  data.cybersearching.net #[qsrch.net][Wildcard DNS]
127.0.0.1  hit.elevonsearch.com
127.0.0.1  www.elevonsearch.com
127.0.0.1  clicks.emarketmakers.com
127.0.0.1  www.enconfidence.com #[Enconfidence]
127.0.0.1  search.findsall.info
127.0.0.1  www.findallresults.net #[qsrch.net]
127.0.0.1  hit.getyourdatahere.com
127.0.0.1  www.getyourdatahere.com
127.0.0.1  find.greatsearch.info
127.0.0.1  result.goodsearch.info
127.0.0.1  www.esearchandfind.org
127.0.0.1  clicks.jackpot.com
127.0.0.1  www.jackpot.com #[MVPS.Criteria][SiteAdvisor.jackpot.com]
127.0.0.1  hit.lookupanything.biz #[qsrch.net]
127.0.0.1  ads.mydailyhoroscope.net #[SunBelt.MyDailyHoroscope]
127.0.0.1  clicks.mydailyhoroscope.net #[ADW_MYDLYSCOPE.A]
127.0.0.1  www.mydailyhoroscope.net #[Adware.Horoscope]
127.0.0.1  www.myphonebillsavings.com
127.0.0.1  www.mysearchnet.org
127.0.0.1  www.new.chat.new.net
127.0.0.1  eps.new.search.new.net
127.0.0.1  client.newdotnet.net
127.0.0.1  client.new.tech.new.net
127.0.0.1  www.firstlook.movie.new.net
127.0.0.1  upgrade.newdotnet.net
127.0.0.1  upgrade.new.tech.new.net
127.0.0.1  www.newdotnet.com #[[eTrust.New.Net.Domain.Plugin]]
127.0.0.1  www.new.net #[McAfee.Adware.NDotNet][ADW_NEWNET.A]
127.0.0.1  www.onestepsearch.net
127.0.0.1  www.onestepsearch.biz
127.0.0.1  adopt.precisead.com #[SpySweeper.Spy.Cookie]
127.0.0.1  blue.qsrch.net
127.0.0.1  pjn.qsrch.net
127.0.0.1  search.qsrch.net
127.0.0.1  www.qsrch.net #[Spyware.QuickSearch]
127.0.0.1  2cool.qsrch.com #[SpySweeper.Spy.Cookie]
127.0.0.1  bgw.qsrch.com
127.0.0.1  dash.qsrch.com #[qsrch.net]
127.0.0.1  hp.qsrch.com
127.0.0.1  moniker.qsrch.com
127.0.0.1  newnet.qsrch.com #[Panda.Spyware:Cookie/Qsrch]
127.0.0.1  nnsearch.qsrch.com
127.0.0.1  regfly.qsrch.com
127.0.0.1  rg.qsrch.com
127.0.0.1  search.qsrch.com
127.0.0.1  worldwide.qsrch.com
127.0.0.1  www.qsrch.com #[SiteAdvisor.qsrch.com]
127.0.0.1  quick.qsrch.info #[AdWare.Toolbar.Quick.a][server down?]
127.0.0.1  www.quickbrowsersearch.com #[McAfee.Adware-Quickbar.dr]
127.0.0.1  data.quicksearches.net
127.0.0.1  find.reliableresults.info #[McAfee.Adware-NDotNet]
127.0.0.1  quick.searchfromyourbrowser.net #[qsrch.net]
127.0.0.1  www.stop-passing-gas.com
127.0.0.1  trafficmarketplace.com #[SunBelt.TrafficMarketplace]
127.0.0.1  sp.trafficmarketplace.com
127.0.0.1  www.trafficmarketplace.com
127.0.0.1  trafficmp.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ad.trafficmp.com #[eTrust.Tracking.Cookie]
127.0.0.1  cache.trafficmp.com #[SpySweeper.Spy.Cookie][p.mii.instacontent.net]
127.0.0.1  images.trafficmp.com #[SunBelt.Trafficmp.com]
127.0.0.1  t.trafficmp.com #[McAfee.Cookie-Trafficmp]
127.0.0.1  ads.uproar.com
127.0.0.1  clicks.uproar.com #[SpySweeper.Spy.Cookie]
127.0.0.1  ads.vendaregroup.com #[Parasite.Enconfidence]
127.0.0.1  adimages.vendaregroup.com
127.0.0.1  dpweb.vendaregroup.com
127.0.0.1  registration.vendaregroup.com
127.0.0.1  hit.virtualsearches.net
127.0.0.1  www.virtualsearches.net
127.0.0.1  www.winantispyware2006.com #[spywareremovall.net]
127.0.0.1  web.yoursearchfinder.com
# [Versimedia, Inc][Webmetro]
127.0.0.1  client.roiadtracker.com
127.0.0.1  toolbar.versimedia.com #[eTrust.MegaToolbar]
# [Vertical Theories][Thought Convergence, Inc][AKA Domains][Ammar Kubba]
127.0.0.1  www.chk-web.com #[ADW_SECTHOUGHT.B]
127.0.0.1  www.cpalist.com
127.0.0.1  fast-finder.com #[HJTH.PowerStrip]
127.0.0.1  www.fast-finder.com #[Adware.FFToolBar]
127.0.0.1  www.danetport.com #[BackDoor-BDI][Win32.Daqa.C]
127.0.0.1  www.ddupdates.com
127.0.0.1  www.dnsstat.net #[TROJ_AGENT.II]
127.0.0.1  www.infport.com #[Troj/SecondT-AA]
127.0.0.1  www.mp3greed.com #[Parked?]
127.0.0.1  mrfindalot.com #[McAfee.Adware-LinkMaker]
127.0.0.1  www.mrfindalot.com #[Trojan-Clicker.Agent.3][Win32/Adware.Suggestor]
127.0.0.1  www.net-check.net
127.0.0.1  www.nextern.net
127.0.0.1  www.newinf.net
127.0.0.1  server.personalmoneytree.com #[AdWare.Win32.MDH.e]
127.0.0.1  www.personalmoneytree.com #[SunBelt.PersonalMoneyTree]
127.0.0.1  www.qklinkserver.com #[SunBelt.QuickLinks][AdWare.Win32.Suggestor.o]
127.0.0.1  www.search4things.com #[srch-results.com]
127.0.0.1  www.serverlogic3.com #[Parasite.Hyperlinker][Adware.LinkMaker]
127.0.0.1  sitesuggestor.com #[seek2.com]
127.0.0.1  www.sitesuggestor.com #[landings.trafficz.com]
127.0.0.1  srch-results.com #[AdWare.Win32.Suggestor.o]
127.0.0.1  search1.srch-results.com
127.0.0.1  www.srch-results.com #[McAfee.Adware-FFinder]
127.0.0.1  thecommunicator.net #[McAfee.Adware-FFinder]
127.0.0.1  www.thecommunicator.net #[Backdoor.Win32.Agent.bg]
127.0.0.1  landing.trafficz.com #[Microsoft.Typo-Patrol]
127.0.0.1  landings.trafficz.com
127.0.0.1  rcom.trafficz.com
127.0.0.1  verticaltheories.com
127.0.0.1  www.verticaltheories.com
127.0.0.1  verschk.com #[Parasite.PowerStrip]
127.0.0.1  www.verschk.com
127.0.0.1  www.webnetinfo.net #[BackDoor-BDI][Spyware.Goidr][Parked?]
# [Vibrant Media]
127.0.0.1  intellitxt.com
127.0.0.1  de.intellitxt.com
127.0.0.1  uk.intellitxt.com
127.0.0.1  us.intellitxt.com
127.0.0.1  www.intellitxt.com
127.0.0.1  atspace.de.intellitxt.com
127.0.0.1  awardspace.de.intellitxt.com
127.0.0.1  computerbase.de.intellitxt.com
127.0.0.1  computerhilfen.de.intellitxt.com
127.0.0.1  computerwoche.de.intellitxt.com
127.0.0.1  digital-world.de.intellitxt.com
127.0.0.1  golem.de.intellitxt.com
127.0.0.1  gulli.de.intellitxt.com
127.0.0.1  images.intellitxt.com
127.0.0.1  inquake.de.intellitxt.com
127.0.0.1  macwelt.de.intellitxt.com
127.0.0.1  pcwelt.de.intellitxt.com
127.0.0.1  php-mag.de.intellitxt.com
127.0.0.1  php-magnet.de.intellitxt.com
127.0.0.1  softonic.de.intellitxt.com
127.0.0.1  supportnet.de.intellitxt.com
127.0.0.1  tecchannel.de.intellitxt.com
127.0.0.1  winfuture.de.intellitxt.com
127.0.0.1  actualite-de-stars.fr.intellitxt.com
127.0.0.1  froggytest.fr.intellitxt.com
127.0.0.1  generation-nt.fr.intellitxt.com
127.0.0.1  infos-du-net.fr.intellitxt.com
127.0.0.1  memoclic.fr.intellitxt.com
127.0.0.1  neteco.fr.intellitxt.com
127.0.0.1  pcinpact.fr.intellitxt.com
127.0.0.1  presence-pc.fr.intellitxt.com
127.0.0.1  programme-tv.fr.intellitxt.com
127.0.0.1  reseaux-telecoms.fr.intellitxt.com
127.0.0.1  tomshardware.fr.intellitxt.com
127.0.0.1  vtrhardware.fr.intellitxt.com
127.0.0.1  zataz.fr.intellitxt.com
127.0.0.1  telefonino.it.intellitxt.com
127.0.0.1  topdownloads.nl.intellitxt.com
127.0.0.1  webwereld.nl.intellitxt.com
127.0.0.1  4thegame.uk.intellitxt.com
127.0.0.1  bink.uk.intellitxt.com
127.0.0.1  biosmagazine.uk.intellitxt.com
127.0.0.1  cbronline.uk.intellitxt.com
127.0.0.1  computeractive.uk.intellitxt.com
127.0.0.1  contactmusic.uk.intellitxt.com
127.0.0.1  digit-life.uk.intellitxt.com
127.0.0.1  femalefirst.uk.intellitxt.com
127.0.0.1  ferrago.uk.intellitxt.com
127.0.0.1  footymad.uk.intellitxt.com
127.0.0.1  freedownloadcenter.uk.intellitxt.com
127.0.0.1  freedownloadmanager.uk.intellitxt.com
127.0.0.1  freewarepalm.uk.intellitxt.com
127.0.0.1  gamesindustry.uk.intellitxt.com
127.0.0.1  hexus.uk.intellitxt.com
127.0.0.1  itreviews.uk.intellitxt.com
127.0.0.1  letsgodigital.uk.intellitxt.com
127.0.0.1  lse.uk.intellitxt.com
127.0.0.1  monstersandcritics.uk.intellitxt.com
127.0.0.1  newlaunches.uk.intellitxt.com
127.0.0.1  nodevice.uk.intellitxt.com
127.0.0.1  pcadvisor.uk.intellitxt.com
127.0.0.1  physorg.uk.intellitxt.com
127.0.0.1  playfuls.uk.intellitxt.com
127.0.0.1  pocketlint.uk.intellitxt.com
127.0.0.1  softpedia.uk.intellitxt.com
127.0.0.1  squarefootball.uk.intellitxt.com
127.0.0.1  tcmagazine.uk.intellitxt.com
127.0.0.1  teamtalk.uk.intellitxt.com
127.0.0.1  thehollywoodnews.uk.intellitxt.com
127.0.0.1  vnunet.uk.intellitxt.com
127.0.0.1  webuser.uk.intellitxt.com
127.0.0.1  wi-fitechnology.uk.intellitxt.com
127.0.0.1  worldtravelguide.uk.intellitxt.com
127.0.0.1  1src.us.intellitxt.com
127.0.0.1  1up.us.intellitxt.com
127.0.0.1  2spyware.us.intellitxt.com
127.0.0.1  24wrestling.us.intellitxt.com
127.0.0.1  411mania.us.intellitxt.com
127.0.0.1  4w-wrestling.us.intellitxt.com
127.0.0.1  5starsupport.us.intellitxt.com
127.0.0.1  9down.us.intellitxt.com
127.0.0.1  able2know.us.intellitxt.com
127.0.0.1  aclasscelebs.us.intellitxt.com
127.0.0.1  activewin.us.intellitxt.com
127.0.0.1  actionscript.us.intellitxt.com
127.0.0.1  advancedmn.us.intellitxt.com
127.0.0.1  adwarereport.us.intellitxt.com
127.0.0.1  afterdawn.us.intellitxt.com
127.0.0.1  afraidtoask.us.intellitxt.com
127.0.0.1  akihabaranews.us.intellitxt.com
127.0.0.1  albinoblacksheep.us.intellitxt.com
127.0.0.1  alive.us.intellitxt.com
127.0.0.1  allhiphop.us.intellitxt.com
127.0.0.1  allrefer.us.intellitxt.com
127.0.0.1  amdzone.us.intellitxt.com
127.0.0.1  americanmedia.us.intellitxt.com
127.0.0.1  andpop.us.intellitxt.com
127.0.0.1  appscout.us.intellitxt.com
127.0.0.1  artistdirect.us.intellitxt.com
127.0.0.1  askmen.us.intellitxt.com
127.0.0.1  askmen2.us.intellitxt.com
127.0.0.1  aquasoft.us.intellitxt.com
127.0.0.1  architecturaldesigns.us.intellitxt.com
127.0.0.1  autoforumuniverse.us.intellitxt.com
127.0.0.1  away.us.intellitxt.com
127.0.0.1  aximsite.us.intellitxt.com
127.0.0.1  bargainpda.us.intellitxt.com
127.0.0.1  baselinemag.us.intellitxt.com
127.0.0.1  betanews.us.intellitxt.com
127.0.0.1  beyondhollywood.us.intellitxt.com
127.0.0.1  bigsoccer.us.intellitxt.com
127.0.0.1  blabbermouth.us.intellitxt.com
127.0.0.1  blastro.us.intellitxt.com
127.0.0.1  bleepingcomputer.us.intellitxt.com
127.0.0.1  bluechillies.us.intellitxt.com
127.0.0.1  boxofficeprophets.us.intellitxt.com
127.0.0.1  brothersoft.us.intellitxt.com
127.0.0.1  bumpshack.us.intellitxt.com
127.0.0.1  businessknowhow.us.intellitxt.com
127.0.0.1  bolt.us.intellitxt.com
127.0.0.1  canmag.us.intellitxt.com
127.0.0.1  cdreviews.us.intellitxt.com
127.0.0.1  cdrinfo.us.intellitxt.com
127.0.0.1  celebrity-babies.us.intellitxt.com
127.0.0.1  celebrityhack.us.intellitxt.com
127.0.0.1  celebritysmackblog.us.intellitxt.com
127.0.0.1  celebscentral.us.intellitxt.com
127.0.0.1  celebrity-gossip.us.intellitxt.com
127.0.0.1  celebritywonder.us.intellitxt.com
127.0.0.1  cheatcc.us.intellitxt.com
127.0.0.1  cheatingdome.us.intellitxt.com
127.0.0.1  cmp.us.intellitxt.com
127.0.0.1  cnet.us.intellitxt.com
127.0.0.1  collegefootballnews.us.intellitxt.com
127.0.0.1  comicbookresources.us.intellitxt.com
127.0.0.1  comingsoon.us.intellitxt.com
127.0.0.1  compnet.us.intellitxt.com
127.0.0.1  consumerreview.us.intellitxt.com
127.0.0.1  cooksrecipes.us.intellitxt.com
127.0.0.1  cooltechzone.us.intellitxt.com
127.0.0.1  countryweekly.us.intellitxt.com
127.0.0.1  coxtv.us.intellitxt.com
127.0.0.1  crmbuyer.us.intellitxt.com
127.0.0.1  csharpcorner.us.intellitxt.com
127.0.0.1  csnation.us.intellitxt.com
127.0.0.1  ctv.us.intellitxt.com
127.0.0.1  dabcc.us.intellitxt.com
127.0.0.1  dailystab.us.intellitxt.com
127.0.0.1  damnimcute.us.intellitxt.com
127.0.0.1  danasdirt.us.intellitxt.com
127.0.0.1  daniweb.us.intellitxt.com
127.0.0.1  darkhorizons.us.intellitxt.com
127.0.0.1  darlamack.us.intellitxt.com
127.0.0.1  dbtechno.us.intellitxt.com
127.0.0.1  demonews.us.intellitxt.com
127.0.0.1  denguru.us.intellitxt.com
127.0.0.1  derekhail.us.intellitxt.com
127.0.0.1  designtechnica.us.intellitxt.com
127.0.0.1  devshed.us.intellitxt.com
127.0.0.1  digitalmediaonline.us.intellitxt.com
127.0.0.1  digitaltrends.us.intellitxt.com
127.0.0.1  dlmag.us.intellitxt.com
127.0.0.1  drdobbs.us.intellitxt.com
127.0.0.1  driverguide.us.intellitxt.com
127.0.0.1  drugscom.us.intellitxt.com
127.0.0.1  eastsideboxing.us.intellitxt.com
127.0.0.1  ecanadanow.us.intellitxt.com
127.0.0.1  ecommercetimes.us.intellitxt.com
127.0.0.1  eepn.us.intellitxt.com
127.0.0.1  efanguide.us.intellitxt.com
127.0.0.1  ehomeupgrade.us.intellitxt.com
127.0.0.1  ehow.us.intellitxt.com
127.0.0.1  entrepreneur.us.intellitxt.com
127.0.0.1  estelle.us.intellitxt.com
127.0.0.1  eten-users.us.intellitxt.com
127.0.0.1  eweek.us.intellitxt.com
127.0.0.1  examnotes.us.intellitxt.com
127.0.0.1  excite.us.intellitxt.com
127.0.0.1  experts.us.intellitxt.com
127.0.0.1  extntechnologies.us.intellitxt.com
127.0.0.1  extremetech.us.intellitxt.com
127.0.0.1  eztracks.us.intellitxt.com
127.0.0.1  fangoria.us.intellitxt.com
127.0.0.1  faqts.us.intellitxt.com
127.0.0.1  fatbackandcollards.us.intellitxt.com
127.0.0.1  fatfreekitchen.us.intellitxt.com
127.0.0.1  fhmonline.us.intellitxt.com
127.0.0.1  filedudes.us.intellitxt.com
127.0.0.1  filmstew.us.intellitxt.com
127.0.0.1  filmthreat.us.intellitxt.com
127.0.0.1  firingsquad.us.intellitxt.com
127.0.0.1  flashmagazine.us.intellitxt.com
127.0.0.1  flexbeta.us.intellitxt.com
127.0.0.1  forbes.us.intellitxt.com
127.0.0.1  foxnews.us.intellitxt.com
127.0.0.1  foxtv.us.intellitxt.com
127.0.0.1  freecodecs.us.intellitxt.com
127.0.0.1  freewarefiles.us.intellitxt.com
127.0.0.1  freewarehome.us.intellitxt.com
127.0.0.1  friendtest.us.intellitxt.com
127.0.0.1  futurelooks.us.intellitxt.com
127.0.0.1  g2.us.intellitxt.com
127.0.0.1  g3.us.intellitxt.com
127.0.0.1  g4.us.intellitxt.com
127.0.0.1  g5.us.intellitxt.com
127.0.0.1  gamedev.us.intellitxt.com
127.0.0.1  gamesradar.us.intellitxt.com
127.0.0.1  gamerstemple.us.intellitxt.com
127.0.0.1  gabsmash.us.intellitxt.com
127.0.0.1  geekstogo.us.intellitxt.com
127.0.0.1  givememyremote.us.intellitxt.com
127.0.0.1  gonintendo.us.intellitxt.com
127.0.0.1  gsmarena.us.intellitxt.com
127.0.0.1  gtmedia.us.intellitxt.com
127.0.0.1  gtrforums.us.intellitxt.com
127.0.0.1  guru3d.us.intellitxt.com
127.0.0.1  hackedgadgets.us.intellitxt.com
127.0.0.1  hardcoreware.us.intellitxt.com
127.0.0.1  hardforum.us.intellitxt.com
127.0.0.1  hardocp.us.intellitxt.com
127.0.0.1  hardwareanalysis.us.intellitxt.com
127.0.0.1  hardwarezone.us.intellitxt.com
127.0.0.1  highdefforum.us.intellitxt.com
127.0.0.1  hiphopdx.us.intellitxt.com
127.0.0.1  hitsquad.us.intellitxt.com
127.0.0.1  hollyrude.us.intellitxt.com
127.0.0.1  hollywood.us.intellitxt.com
127.0.0.1  hollywoodbackwash.us.intellitxt.com
127.0.0.1  hollywoodtuna.us.intellitxt.com
127.0.0.1  hometheaterhifi.us.intellitxt.com
127.0.0.1  hondahookup.us.intellitxt.com
127.0.0.1  hoopsvibe.us.intellitxt.com
127.0.0.1  hoopsworld.us.intellitxt.com
127.0.0.1  hoovers.us.intellitxt.com
127.0.0.1  hostboard.us.intellitxt.com
127.0.0.1  hothardware.us.intellitxt.com
127.0.0.1  hotmommagossip.us.intellitxt.com
127.0.0.1  hotonlinenews.us.intellitxt.com
127.0.0.1  howardchui.us.intellitxt.com
127.0.0.1  htmlcenter.us.intellitxt.com
127.0.0.1  i4u.us.intellitxt.com
127.0.0.1  iamnotageek.us.intellitxt.com
127.0.0.1  icentric.us.intellitxt.com
127.0.0.1  ichef.us.intellitxt.com
127.0.0.1  icydk.us.intellitxt.com
127.0.0.1  idontlikeyouinthatway.us.intellitxt.com
127.0.0.1  iesb.us.intellitxt.com
127.0.0.1  ifmagazine.us.intellitxt.com
127.0.0.1  ign.us.intellitxt.com
127.0.0.1  babes.ign.us.intellitxt.com
127.0.0.1  cars.ign.us.intellitxt.com
127.0.0.1  comics.ign.us.intellitxt.com
127.0.0.1  cube.ign.us.intellitxt.com
127.0.0.1  ds.ign.us.intellitxt.com
127.0.0.1  filmforcedvd.ign.us.intellitxt.com
127.0.0.1  gameboy.ign.us.intellitxt.com
127.0.0.1  gear.ign.us.intellitxt.com
127.0.0.1  music.ign.us.intellitxt.com
127.0.0.1  psp.ign.us.intellitxt.com
127.0.0.1  ps2.ign.us.intellitxt.com
127.0.0.1  ps3.ign.us.intellitxt.com
127.0.0.1  psx.ign.us.intellitxt.com
127.0.0.1  revolution.ign.us.intellitxt.com
127.0.0.1  sports.ign.us.intellitxt.com
127.0.0.1  wireless.ign.us.intellitxt.com
127.0.0.1  xbox.ign.us.intellitxt.com
127.0.0.1  xbox360.ign.us.intellitxt.com
127.0.0.1  idm.us.intellitxt.com
127.0.0.1  i-hacked.us.intellitxt.com
127.0.0.1  imnotobsessed.us.intellitxt.com
127.0.0.1  impactwrestling.us.intellitxt.com
127.0.0.1  insidemacgames.us.intellitxt.com
127.0.0.1  intermix.us.intellitxt.com
127.0.0.1  intogossip.us.intellitxt.com
127.0.0.1  investopedia.us.intellitxt.com
127.0.0.1  ittoolbox.us.intellitxt.com
127.0.0.1  itxt2.us.intellitxt.com
127.0.0.1  itxt3.us.intellitxt.com
127.0.0.1  ivillage.us.intellitxt.com
127.0.0.1  s.ivillage.us.intellitxt.com
127.0.0.1  iwon.us.intellitxt.com
127.0.0.1  jakeludington.us.intellitxt.com
127.0.0.1  javaworld.us.intellitxt.com
127.0.0.1  jkontherun.us.intellitxt.com
127.0.0.1  joblo.us.intellitxt.com
127.0.0.1  juicy-news.blogspot.us.intellitxt.com
127.0.0.1  jupiter.us.intellitxt.com
127.0.0.1  justmovietrailers.us.intellitxt.com
127.0.0.1  kaboose.us.intellitxt.com
127.0.0.1  knac.us.intellitxt.com
127.0.0.1  laboroflove.us.intellitxt.com
127.0.0.1  laptoplogic.us.intellitxt.com
127.0.0.1  laptopmag.us.intellitxt.com
127.0.0.1  lat34.us.intellitxt.com
127.0.0.1  latinoreview.us.intellitxt.com
127.0.0.1  linuxdevcenter.us.intellitxt.com
127.0.0.1  linuxjournal.us.intellitxt.com
127.0.0.1  lmcd.us.intellitxt.com
127.0.0.1  lockergnome.us.intellitxt.com
127.0.0.1  longhornblogs.us.intellitxt.com
127.0.0.1  lxer.us.intellitxt.com
127.0.0.1  macdailynews.us.intellitxt.com
127.0.0.1  macnewsworld.us.intellitxt.com
127.0.0.1  macnn.us.intellitxt.com
127.0.0.1  macgamefiles.us.intellitxt.com
127.0.0.1  macmegasite.us.intellitxt.com
127.0.0.1  madpenguin.us.intellitxt.com
127.0.0.1  masalatalk.us.intellitxt.com
127.0.0.1  mazdaworld.us.intellitxt.com
127.0.0.1  medicinenet.us.intellitxt.com
127.0.0.1  medindia.us.intellitxt.com
127.0.0.1  memphisrap.us.intellitxt.com
127.0.0.1  meredithtv.us.intellitxt.com
127.0.0.1  methodshop.us.intellitxt.com
127.0.0.1  mobile9.us.intellitxt.com
127.0.0.1  mobileburn.us.intellitxt.com
127.0.0.1  mobiletechreview.us.intellitxt.com
127.0.0.1  mobilewhack.us.intellitxt.com
127.0.0.1  mobilityguru.us.intellitxt.com
127.0.0.1  mobilitysite.us.intellitxt.com
127.0.0.1  morningstar.us.intellitxt.com
127.0.0.1  moviehole.us.intellitxt.com
127.0.0.1  movie-list.us.intellitxt.com
127.0.0.1  movies.us.intellitxt.com
127.0.0.1  movieweb.us.intellitxt.com
127.0.0.1  msfn.us.intellitxt.com
127.0.0.1  sports.msnbc.us.intellitxt.com
127.0.0.1  technology.msnbc.us.intellitxt.com
127.0.0.1  muscleandfitnesshers.us.intellitxt.com
127.0.0.1  myfavoritegames.us.intellitxt.com
127.0.0.1  nasioc.us.intellitxt.com
127.0.0.1  nationalenquirer.us.intellitxt.com
127.0.0.1  naturalhealth.us.intellitxt.com
127.0.0.1  nbcuniversaltv.us.intellitxt.com
127.0.0.1  neoseeker.us.intellitxt.com
127.0.0.1  neowin.us.intellitxt.com
127.0.0.1  ngohq.us.intellitxt.com
127.0.0.1  nihoncar.us.intellitxt.com
127.0.0.1  ninjadude.us.intellitxt.com
127.0.0.1  ntcompatible.us.intellitxt.com
127.0.0.1  obgyn.us.intellitxt.com
127.0.0.1  octools.us.intellitxt.com
127.0.0.1  ocworkbench.us.intellitxt.com
127.0.0.1  onlamp.us.intellitxt.com
127.0.0.1  oocenter.us.intellitxt.com
127.0.0.1  ostg.us.intellitxt.com
127.0.0.1  outofsightmedia.us.intellitxt.com
127.0.0.1  overclockersonline.us.intellitxt.com
127.0.0.1  pcmag.us.intellitxt.com
127.0.0.1  pcper.us.intellitxt.com
127.0.0.1  pencomputing.us.intellitxt.com
127.0.0.1  penton.us.intellitxt.com
127.0.0.1  perezhilton.us.intellitxt.com
127.0.0.1  pimprig.us.intellitxt.com
127.0.0.1  planetgamecube.us.intellitxt.com
127.0.0.1  planet-source-code.us.intellitxt.com
127.0.0.1  popoholic.us.intellitxt.com
127.0.0.1  popmechanics.us.intellitxt.com
127.0.0.1  popularmechanics.us.intellitxt.com
127.0.0.1  portableplanet.us.intellitxt.com
127.0.0.1  postchronicle.us.intellitxt.com
127.0.0.1  prettyboring.us.intellitxt.com
127.0.0.1  priusonline.us.intellitxt.com
127.0.0.1  profootballweekly.us.intellitxt.com
127.0.0.1  pro-networks.us.intellitxt.com
127.0.0.1  punchjump.us.intellitxt.com
127.0.0.1  pwinsider.us.intellitxt.com
127.0.0.1  qj.us.intellitxt.com
127.0.0.1  rawstory.us.intellitxt.com
127.0.0.1  rcpmag.us.intellitxt.com
127.0.0.1  recipegoldmine.us.intellitxt.com
127.0.0.1  recipeland.us.intellitxt.com
127.0.0.1  roadcatalogs.us.intellitxt.com
127.0.0.1  rojakpot.us.intellitxt.com
127.0.0.1  rpg.us.intellitxt.com
127.0.0.1  rx8club.us.intellitxt.com
127.0.0.1  rydium.us.intellitxt.com
127.0.0.1  screensavers.us.intellitxt.com
127.0.0.1  sdtimes.us.intellitxt.com
127.0.0.1  siliconera.us.intellitxt.com
127.0.0.1  slashfilm.us.intellitxt.com
127.0.0.1  slashphone.us.intellitxt.com
127.0.0.1  soccergaming.us.intellitxt.com
127.0.0.1  soft32.us.intellitxt.com
127.0.0.1  sohh.us.intellitxt.com
127.0.0.1  somethingawful.us.intellitxt.com
127.0.0.1  soundslam.us.intellitxt.com
127.0.0.1  speedguide.us.intellitxt.com
127.0.0.1  speedtv.us.intellitxt.com
127.0.0.1  sprintusers.us.intellitxt.com
127.0.0.1  spymac.us.intellitxt.com
127.0.0.1  sqlservercentral.us.intellitxt.com
127.0.0.1  starpulse.us.intellitxt.com
127.0.0.1  stockgroup.us.intellitxt.com
127.0.0.1  storknet.us.intellitxt.com
127.0.0.1  supercars.us.intellitxt.com
127.0.0.1  superherohype.us.intellitxt.com
127.0.0.1  surebaby.us.intellitxt.com
127.0.0.1  symbianone.us.intellitxt.com
127.0.0.1  symbian-freak.us.intellitxt.com
127.0.0.1  tastefulcelebs.us.intellitxt.com
127.0.0.1  techeblog.us.intellitxt.com
127.0.0.1  tech-faq.us.intellitxt.com
127.0.0.1  techgage.us.intellitxt.com
127.0.0.1  techguy.us.intellitxt.com
127.0.0.1  techpowerup.us.intellitxt.com
127.0.0.1  techspot.us.intellitxt.com
127.0.0.1  technewsworld.us.intellitxt.com
127.0.0.1  tenmagazines.us.intellitxt.com
127.0.0.1  theblemish.us.intellitxt.com
127.0.0.1  thebosh.us.intellitxt.com
127.0.0.1  thecarconnection.us.intellitxt.com
127.0.0.1  thecelebritycafe.us.intellitxt.com
127.0.0.1  theeldergeek.us.intellitxt.com
127.0.0.1  thefinalfantasy.us.intellitxt.com
127.0.0.1  theforce.us.intellitxt.com
127.0.0.1  thefutoncritic.us.intellitxt.com
127.0.0.1  thegauntlet.us.intellitxt.com
127.0.0.1  thehollywoodgossip.us.intellitxt.com
127.0.0.1  themanroom.us.intellitxt.com
127.0.0.1  theonenetwork.us.intellitxt.com
127.0.0.1  thesuperficial.us.intellitxt.com
127.0.0.1  thetechlounge.us.intellitxt.com
127.0.0.1  thetechzone.us.intellitxt.com
127.0.0.1  theunwired.us.intellitxt.com
127.0.0.1  thinkcomputers.us.intellitxt.com
127.0.0.1  thoughtsmedia.us.intellitxt.com
127.0.0.1  threadwatch.us.intellitxt.com
127.0.0.1  toms.us.intellitxt.com
127.0.0.1  tomsforumz.us.intellitxt.com
127.0.0.1  tomsnetworking.us.intellitxt.com
127.0.0.1  tothecenter.us.intellitxt.com
127.0.0.1  tradingmarkets.us.intellitxt.com
127.0.0.1  tribal.us.intellitxt.com
127.0.0.1  tutorialoutpost.us.intellitxt.com
127.0.0.1  tweaktown.us.intellitxt.com
127.0.0.1  twitchguru.us.intellitxt.com
127.0.0.1  ultimate-guitar.us.intellitxt.com
127.0.0.1  upi.us.intellitxt.com
127.0.0.1  vault9.us.intellitxt.com
127.0.0.1  viaarena.us.intellitxt.com
127.0.0.1  vidnet.us.intellitxt.com
127.0.0.1  voodoofiles.us.intellitxt.com
127.0.0.1  warcry.us.intellitxt.com
127.0.0.1  warp2search.us.intellitxt.com
127.0.0.1  wdxcyber.us.intellitxt.com
127.0.0.1  wincert.us.intellitxt.com
127.0.0.1  winmatrix.us.intellitxt.com
127.0.0.1  wm5fixsite.us.intellitxt.com
127.0.0.1  womensforum.us.intellitxt.com
127.0.0.1  worldnetdaily.us.intellitxt.com
127.0.0.1  x17online.us.intellitxt.com
127.0.0.1  xmlpitstop.us.intellitxt.com
127.0.0.1  yeeeah.us.intellitxt.com
127.0.0.1  zatznotfunny.us.intellitxt.com
127.0.0.1  zug.us.intellitxt.com
127.0.0.1  betanews.us.smarttargetting.com
127.0.0.1  xbitlabs.us.smarttargetting.com
127.0.0.1  www.smarttargetting.com
127.0.0.1  vibrantmedia.com
127.0.0.1  itxt.vibrantmedia.com
127.0.0.1  usads.vibrantmedia.com
127.0.0.1  usnews.vibrantmedia.com
127.0.0.1  www.vibrantmedia.com
# [vioCLICKS][Xstats, Inc]
127.0.0.1  hit1.vioclicks.com #[SunBelt.VioClicks.com]
127.0.0.1  view1.vioclicks.com
127.0.0.1  www.vioclicks.com #[eTrust.VioClicks]
127.0.0.1  hit1.xstats.com
127.0.0.1  view1.xstats.com
# [Virtumundo, INC]
127.0.0.1  virtumundo.com #[Panda.Virtumonde.C]
127.0.0.1  my.virtumundo.com
127.0.0.1  privacy.virtumundo.com
127.0.0.1  redirect.virtumundo.com
127.0.0.1  www.virtumundo.com #[TROJ_AGENT.BN]
127.0.0.1  vmadmin.com
127.0.0.1  www.vtarget.com
# [Warren Vert]
127.0.0.1  freeaccessbar.com #[Adware.FreeAccessBar]
127.0.0.1  www.freeaccessbar.com #[adw.Petro-Line.FreeAccessBar]
127.0.0.1  topmoviezone.com
127.0.0.1  www.topmoviezone.com
# [Webads Europe]
127.0.0.1  storage.adsolutions.nl
127.0.0.1  telgids.adsolutions.nl
127.0.0.1  adserver.webads.nl
127.0.0.1  images.webads.nl
# [WebDevAZ, Inc]
127.0.0.1  dl.ezthemes.com #[AdWare.Win32.WebRebates.p]
127.0.0.1  dl1.ezthemes.com #[Trojan-Downloader.Win32.Small.bke]
127.0.0.1  ezthemes.ezthemes.com #[StopBadware.ezthemes]
127.0.0.1  funskins.ezthemes.com
127.0.0.1  galtthemes.ezthemes.com
127.0.0.1  themexp.ezthemes.com
127.0.0.1  topdesktop.ezthemes.com
127.0.0.1  www.ezthemes.com #[SiteAdvisor.ezthemes.com]
127.0.0.1  dl2.themexp.org
127.0.0.1  www.themexp.org #[StopBadware.Warning]
# [Webhancer Corp][Spyware.Webhancer]
127.0.0.1  www.realenduser.com
127.0.0.1  a1.webhancer.com #[SiteAdvisor.webhancer.com]
127.0.0.1  d.webhancer.com
127.0.0.1  d2.webhancer.com
127.0.0.1  d3.webhancer.com
127.0.0.1  download.webhancer.com
127.0.0.1  dr1.webhancer.com #[McAfee.Spyware-WebHancer.dr]
127.0.0.1  dr2.webhancer.com
127.0.0.1  prime.webhancer.com
127.0.0.1  reports.webhancer.com
127.0.0.1  server.webhancer.com
127.0.0.1  update.webhancer.com #[SPYW_WEBHANCER.A]
127.0.0.1  b1-v2-bell.webhancer.com
127.0.0.1  b2-v1-bell.webhancer.com
127.0.0.1  b3-v1-bell.webhancer.com
127.0.0.1  secondary.webhancer.com
127.0.0.1  vr1-v1.webhancer.com
127.0.0.1  vws-1.webhancer.com #[AdWare.Win32.WebHancer.381]
127.0.0.1  www.webhancer.com #[SunBelt.webHancer]
# [Webnet International]
127.0.0.1  bannerco-op.com
127.0.0.1  bannersgomlm.com
127.0.0.1  www.bannersgomlm.com
127.0.0.1  bannersgomlm.buildreferrals.com
# [Web Services]
127.0.0.1  banner.50megs.com
127.0.0.1  free-counter.5u.com
127.0.0.1  get-antispyware.5u.com #[Malicious.Links.winantispyware.com]
127.0.0.1  hit-counter.5u.com
127.0.0.1  web-counter.5u.com
127.0.0.1  aboutwebservices.com
127.0.0.1  freestats.com
127.0.0.1  banner.freeservers.com
127.0.0.1  eegad.freeservers.com #[SpySweeper.Spy.Cookie]
127.0.0.1  free-stats.i8.com
127.0.0.1  site-stats.i8.com
127.0.0.1  sitetracker.com
127.0.0.1  pomeranian99.sitetracker.com
127.0.0.1  www.sitetracker.com
127.0.0.1  www2a.sitetracker.com
# [WebSideStory, Inc][Tracking Service]
127.0.0.1  hitbox.com
127.0.0.1  ai.hitbox.com
127.0.0.1  aibg.hitbox.com
127.0.0.1  counter.hitbox.com
127.0.0.1  ehg.hitbox.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  ehg-aarp.hitbox.com
127.0.0.1  ehg-adaptivemarketing.hitbox.com
127.0.0.1  ehg-adteractive.hitbox.com
127.0.0.1  ehg-adversitement.hitbox.com
127.0.0.1  ehg-agency.hitbox.com
127.0.0.1  ehg-aha.hitbox.com #[Tenebril.Tracking.Cookie]
127.0.0.1  ehg-akagourmet.hitbox.com
127.0.0.1  ehg-alt64.hitbox.com
127.0.0.1  ehg-apollogroup.hitbox.com
127.0.0.1  ehg-aspca.hitbox.com
127.0.0.1  ehg-associatednewmedia.hitbox.com
127.0.0.1  ehg-ati.hitbox.com
127.0.0.1  ehg-att2.hitbox.com
127.0.0.1  ehg-attcorp.hitbox.com
127.0.0.1  ehg-autodesk.hitbox.com
127.0.0.1  ehg-autotrader.hitbox.com
127.0.0.1  ehg-autozone.hitbox.com
127.0.0.1  ehg-backweb.hitbox.com
127.0.0.1  ehg-bandwidth.hitbox.com
127.0.0.1  ehg-barclaysglobal.hitbox.com
127.0.0.1  ehg-bareweb.hitbox.com
127.0.0.1  ehg-bbc.hitbox.com
127.0.0.1  ehg-bce.hitbox.com
127.0.0.1  ehg-bestbuy.hitbox.com
127.0.0.1  ehg-bestwestern.hitbox.com
127.0.0.1  ehg-bizjournals.hitbox.com
127.0.0.1  ehg-borgata.hitbox.com
127.0.0.1  ehg-bskyb.hitbox.com
127.0.0.1  ehg-cafepress.hitbox.com
127.0.0.1  ehg-camcorderinfo.hitbox.com
127.0.0.1  ehg-campmor.hitbox.com
127.0.0.1  ehg-cardomain.hitbox.com
127.0.0.1  ehg-cbc.hitbox.com
127.0.0.1  ehg-cbs.hitbox.com
127.0.0.1  ehg-centaur.hitbox.com
127.0.0.1  ehg-cisco.hitbox.com #[SunBelt.Ehg-Cisco.Hitbox]
127.0.0.1  ehg-channelwave.hitbox.com
127.0.0.1  ehg-chartercommunications.hitbox.com
127.0.0.1  ehg-chcf.hitbox.com
127.0.0.1  ehg-chrysler.hitbox.com
127.0.0.1  ehg-citrixonline.hitbox.com
127.0.0.1  ehg-classifiedventures.hitbox.com
127.0.0.1  ehg-classmates.hitbox.com
127.0.0.1  ehg-clearchannel.hitbox.com
127.0.0.1  ehg-comcast.hitbox.com
127.0.0.1  ehg-cometsystems.hitbox.com
127.0.0.1  ehg-commjun.hitbox.com
127.0.0.1  ehg-copenhagen.hitbox.com
127.0.0.1  ehg-corusentertainment.hitbox.com
127.0.0.1  ehg-crain.hitbox.com
127.0.0.1  ehg-ctv.hitbox.com
127.0.0.1  ehg-cygnusbm.hitbox.com
127.0.0.1  ehg-danskin.hitbox.com
127.0.0.1  ehg-darksideprod.hitbox.com
127.0.0.1  ehg-datamonitor.hitbox.com
127.0.0.1  ehg-deltatre.hitbox.com
127.0.0.1  ehg-ddadigital.hitbox.com
127.0.0.1  ehg-dig.hitbox.com
127.0.0.1  ehg-digg.hitbox.com
127.0.0.1  ehg-dolphins.hitbox.com
127.0.0.1  ehg-electrum.hitbox.com
127.0.0.1  ehg-eline.hitbox.com
127.0.0.1  ehg-equifax.hitbox.com
127.0.0.1  ehg-eset.hitbox.com
127.0.0.1  ehg-findlaw.hitbox.com
127.0.0.1  ehg-foundation.hitbox.com
127.0.0.1  ehg-foxinteractive.hitbox.com
127.0.0.1  ehg-foxmovies.hitbox.com
127.0.0.1  ehg-foxsports.hitbox.com
127.0.0.1  ehg-france24.hitbox.com
127.0.0.1  ehg-freshpairllc.hitbox.com
127.0.0.1  ehg-futurepub.hitbox.com
127.0.0.1  ehg-fxcm.hitbox.com
127.0.0.1  ehg-gamedaily.hitbox.com
127.0.0.1  ehg-gameshownet.hitbox.com
127.0.0.1  ehg-gamespot.hitbox.com
127.0.0.1  ehg-gatehousemedia.hitbox.com
127.0.0.1  ehg-globalgamingleague.hitbox.com
127.0.0.1  ehg-groupernetworks.hitbox.com
127.0.0.1  ehg-harleydavidson.hitbox.com
127.0.0.1  ehg-herenetworks.hitbox.com
127.0.0.1  ehg-hollywoodmedia.hitbox.com
127.0.0.1  ehg-hollywood.hitbox.com
127.0.0.1  ehg-icelandair.hitbox.com
127.0.0.1  ehg-idg.hitbox.com
127.0.0.1  ehg-idgentertainment.hitbox.com
127.0.0.1  ehg-ifilm.hitbox.com #[SiteAdvisor.ifilm.com]
127.0.0.1  ehg-ignitemedia.hitbox.com
127.0.0.1  ehg-imedia.hitbox.com
127.0.0.1  ehg-independent.hitbox.com
127.0.0.1  ehg-intellextinc.hitbox.com
127.0.0.1  ehg-ittoolbox.hitbox.com
127.0.0.1  ehg-itworldcanada.hitbox.com
127.0.0.1  ehg-iwantoneofthose.hitbox.com
127.0.0.1  ehg-jaygroup.hitbox.com
127.0.0.1  ehg-jobster.hitbox.com
127.0.0.1  ehg-kasperskylab.hitbox.com
127.0.0.1  ehg-kingstontechnology.hitbox.com
127.0.0.1  ehg-knightridder.hitbox.com
127.0.0.1  ehg-kodak.hitbox.com
127.0.0.1  ehg-ladbrokes.hitbox.com
127.0.0.1  ehg-learningco.hitbox.com
127.0.0.1  ehg-leapfrog.hitbox.com
127.0.0.1  ehg-legacy.hitbox.com
127.0.0.1  ehg-legonewyorkinc.hitbox.com
127.0.0.1  ehg-lexmark.hitbox.com
127.0.0.1  ehg-linksys.hitbox.com
127.0.0.1  ehg-lls.hitbox.com
127.0.0.1  ehg-lowermybills.hitbox.com #[SiteAdvisor.belnk.com]
127.0.0.1  ehg-majorbaseball.hitbox.com
127.0.0.1  ehg-maniatv.hitbox.com
127.0.0.1  ehg-mattress.hitbox.com
127.0.0.1  ehg-mccormick.hitbox.com
127.0.0.1  ehg-meevee.hitbox.com
127.0.0.1  ehg-metainterfacesllc.hitbox.com
127.0.0.1  ehg-mgmmirageoperations.hitbox.com
127.0.0.1  ehg-mgnlimited.hitbox.com
127.0.0.1  ehg-mh.hitbox.com
127.0.0.1  ehg-micron.hitbox.com
127.0.0.1  ehg-milesmediagroup.hitbox.com
127.0.0.1  ehg-mindshare.hitbox.com
127.0.0.1  ehg-minglematch.hitbox.com
127.0.0.1  ehg-motive.hitbox.com
127.0.0.1  ehg-mshanken.hitbox.com
127.0.0.1  ehg-mtv.hitbox.com
127.0.0.1  ehg-nbif.hitbox.com
127.0.0.1  ehg-nestlepurinapetcare.hitbox.com
127.0.0.1  ehg-nestleusainc.hitbox.com
127.0.0.1  ehg-netapparel.hitbox.com
127.0.0.1  ehg-newegg.hitbox.com
127.0.0.1  ehg-newscientist.hitbox.com
127.0.0.1  ehg-nfusiongroup.hitbox.com
127.0.0.1  ehg-nike.hitbox.com
127.0.0.1  ehg-nokiafin.hitbox.com
127.0.0.1  ehg-northjerseymediagroup.hitbox.com
127.0.0.1  ehg-nvidia.hitbox.com
127.0.0.1  ehg-orangecountyregister.hitbox.com
127.0.0.1  ehg-oreilly.hitbox.com
127.0.0.1  ehg-osiris.hitbox.com
127.0.0.1  ehg-pcsecurityshield.hitbox.com
127.0.0.1  ehg-pennwell.hitbox.com
127.0.0.1  ehg-pfizer.hitbox.com
127.0.0.1  ehg-pharmacia.hitbox.com
127.0.0.1  ehg-pizzahut.hitbox.com
127.0.0.1  ehg-playboy.hitbox.com #[Panda.Spyware:Cookie/Hitbox]
127.0.0.1  ehg-proflowers.hitbox.com
127.0.0.1  ehg-qualcomm.hitbox.com
127.0.0.1  ehg-randomhouse.hitbox.com
127.0.0.1  ehg-redherring.hitbox.com
127.0.0.1  ehg-reed.hitbox.com
127.0.0.1  ehg-rfa.hitbox.com
127.0.0.1  ehg-rodale.hitbox.com
127.0.0.1  ehg-salonmedia.hitbox.com
127.0.0.1  ehg-samsungusa.hitbox.com
127.0.0.1  ehg-saraleeintimate.hitbox.com
127.0.0.1  ehg-schwannssales.hitbox.com
127.0.0.1  ehg-sfcvb.hitbox.com
127.0.0.1  ehg-sharpelectronic.hitbox.com
127.0.0.1  ehg-shoes.hitbox.com
127.0.0.1  ehg-shopathome.hitbox.com
127.0.0.1  ehg-silverpop.hitbox.com
127.0.0.1  ehg-simstar.hitbox.com
127.0.0.1  ehg-sixapart.hitbox.com
127.0.0.1  ehg-sonycomputer.hitbox.com
127.0.0.1  ehg-sonyelec.hitbox.com
127.0.0.1  ehg-sonyesolutions.hitbox.com
127.0.0.1  ehg-sonyeu.hitbox.com
127.0.0.1  ehg-sonyny.hitbox.com
127.0.0.1  ehg-space.hitbox.com #[SunBelt.Ehg-Space.hitbox]
127.0.0.1  ehg-speakeasy.hitbox.com
127.0.0.1  ehg-stampsdotcom.hitbox.com
127.0.0.1  ehg-studentuniverse.hitbox.com
127.0.0.1  ehg-sueddeutsche.hitbox.com
127.0.0.1  ehg-suite101.hitbox.com
127.0.0.1  ehg-superwarehouse.hitbox.com
127.0.0.1  ehg-systemax.hitbox.com
127.0.0.1  ehg-techtarget.hitbox.com
127.0.0.1  ehg-tempurpedic.hitbox.com
127.0.0.1  ehg-tfl.hitbox.com
127.0.0.1  ehg-thegazette.hitbox.com
127.0.0.1  ehg-theheritagefoundation.hitbox.com
127.0.0.1  ehg-theviptour.hitbox.com
127.0.0.1  ehg-thomas.hitbox.com
127.0.0.1  ehg-thomsonhealthcareinc.hitbox.com
127.0.0.1  ehg-ti.hitbox.com
127.0.0.1  ehg-tigerdirect2.hitbox.com
127.0.0.1  ehg-timeinc.hitbox.com
127.0.0.1  ehg-tiscover.hitbox.com
127.0.0.1  ehg-tmgolf.hitbox.com
127.0.0.1  ehg-toditocorp.hitbox.com
127.0.0.1  ehg-topps.hitbox.com
127.0.0.1  ehg-traderpublishing.hitbox.com
127.0.0.1  ehg-traderelectronicmedia.hitbox.com
127.0.0.1  ehg-twi.hitbox.com
127.0.0.1  ehg-u3.hitbox.com
127.0.0.1  ehg-ubid.hitbox.com
127.0.0.1  ehg-ubisoft.hitbox.com
127.0.0.1  ehg-uniontrib.hitbox.com
127.0.0.1  ehg-veohnetworksinc.hitbox.com
127.0.0.1  ehg-viacom.hitbox.com
127.0.0.1  ehg-vmixmediainc.hitbox.com
127.0.0.1  ehg-vmware.hitbox.com
127.0.0.1  ehg-vonage.hitbox.com
127.0.0.1  ehg-wachovia.hitbox.com
127.0.0.1  ehg-warnerbrothers.hitbox.com
127.0.0.1  ehg-webchutney.hitbox.com
127.0.0.1  ehg-websense.hitbox.com
127.0.0.1  ehg-win2000mag.hitbox.com
127.0.0.1  ehg-wsseurope.hitbox.com
127.0.0.1  ehg-wetseal.hitbox.com
127.0.0.1  ehg-wizardsofthecoast.hitbox.com
127.0.0.1  ehg-worldvision.hitbox.com
127.0.0.1  ehg-xandria.hitbox.com
127.0.0.1  ehg-y2m.hitbox.com
127.0.0.1  ehg-yakpak.hitbox.com
127.0.0.1  ehg-youtube.hitbox.com
127.0.0.1  ehg-zazzle.hitbox.com
127.0.0.1  ehg-zentropypartners.hitbox.com
127.0.0.1  ehg-zoom.hitbox.com
127.0.0.1  evwr.hitbox.com
127.0.0.1  get.hitbox.com
127.0.0.1  hg1.hitbox.com #[Trojan-Clicker.Win32.NetBuie.a]
127.0.0.1  hitboxcentral.com
127.0.0.1  ias.hitbox.com
127.0.0.1  ibg.hitbox.com
127.0.0.1  ics.hitbox.com
127.0.0.1  js1.hitbox.com
127.0.0.1  phg.hitbox.com
127.0.0.1  resources.hitbox.com
127.0.0.1  rd1.hitbox.com
127.0.0.1  sitesearch.hitbox.com
127.0.0.1  stats.hitbox.com
127.0.0.1  tools.hitbox.com
127.0.0.1  tools2.hitbox.com
127.0.0.1  vwr1.hitbox.com
127.0.0.1  vwr2.hitbox.com
127.0.0.1  vwr3.hitbox.com
127.0.0.1  w1.hitbox.com
127.0.0.1  w2.hitbox.com
127.0.0.1  w3.hitbox.com
127.0.0.1  w4.hitbox.com
127.0.0.1  w5.hitbox.com #[Ewido.TrackingCookie.Hitbox]
127.0.0.1  w6.hitbox.com
127.0.0.1  w7.hitbox.com
127.0.0.1  w8.hitbox.com
127.0.0.1  w9.hitbox.com
127.0.0.1  w10.hitbox.com
127.0.0.1  w11.hitbox.com
127.0.0.1  w12.hitbox.com
127.0.0.1  w13.hitbox.com
127.0.0.1  w14.hitbox.com
127.0.0.1  w15.hitbox.com
127.0.0.1  w16.hitbox.com
127.0.0.1  w17.hitbox.com
127.0.0.1  w18.hitbox.com
127.0.0.1  w19.hitbox.com
127.0.0.1  w20.hitbox.com
127.0.0.1  w21.hitbox.com
127.0.0.1  w22.hitbox.com
127.0.0.1  w23.hitbox.com
127.0.0.1  w24.hitbox.com
127.0.0.1  w25.hitbox.com
127.0.0.1  w26.hitbox.com
127.0.0.1  w27.hitbox.com
127.0.0.1  w28.hitbox.com
127.0.0.1  w29.hitbox.com
127.0.0.1  w30.hitbox.com
127.0.0.1  w31.hitbox.com
127.0.0.1  w32.hitbox.com
127.0.0.1  w33.hitbox.com
127.0.0.1  w101.hitbox.com
127.0.0.1  w116.hitbox.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  w117.hitbox.com
127.0.0.1  w118.hitbox.com
127.0.0.1  w119.hitbox.com
127.0.0.1  w120.hitbox.com
127.0.0.1  ww2.hitbox.com
127.0.0.1  ww3.hitbox.com
127.0.0.1  wwa.hitbox.com
127.0.0.1  wwc.hitbox.com
127.0.0.1  wwd.hitbox.com
127.0.0.1  www.hitbox.com
127.0.0.1  statmarket.com
127.0.0.1  stats.statmarket.com
127.0.0.1  websidestory.com
127.0.0.1  support.websidestory.com
127.0.0.1  www.websidestory.com #[SunBelt.WebSideStory.com]
# [WebSideStory via Misc Sites]
127.0.0.1  bat.adeptscience.co.uk
127.0.0.1  a.adultentertainmentexpo.com
127.0.0.1  a.advanstar.com
127.0.0.1  c.alladultchannel.com
127.0.0.1  h.allrecipes.com
127.0.0.1  ehg.allstate.com
127.0.0.1  a.americasnetwork.com
127.0.0.1  a.answers.com
127.0.0.1  www-t.apartments.com
127.0.0.1  a.bluewin.ch
127.0.0.1  peach.bskyb.com
127.0.0.1  a.cbc.ca
127.0.0.1  my.clearchannelradio.com
127.0.0.1  a.cricinfo.com #[ehg-cricinfo.hitbox.com]
127.0.0.1  a.csmonitor.com
127.0.0.1  y.digg.com #[ehg-digg.hitbox.com]
127.0.0.1  b.digitmag.co.uk #[ehg-idg.hitbox.com]
127.0.0.1  a.eastvalleytribune.com
127.0.0.1  a.environmentaldefense.org
127.0.0.1  a.fandango.com
127.0.0.1  a.findarticles.com
127.0.0.1  tracking.foxnews.com #[ehg-foxnewsnetworkllc.hitbox.com]
127.0.0.1  h.foxsports.com #[ehg-foxsports.hitbox.com]
127.0.0.1  a.ftd.de
127.0.0.1  iipd.furniturefind.com
127.0.0.1  c.gamelink.com
127.0.0.1  d.hamptonroads.com
127.0.0.1  wss.hbpl.co.uk
127.0.0.1  a.heretv.com
127.0.0.1  ab.idg.se
127.0.0.1  t.ifilm.com
127.0.0.1  a.independent.co.uk
127.0.0.1  h.iwin.com #[ehg-iwin.hitbox.com]
127.0.0.1  hits.gureport.co.uk
127.0.0.1  a.macworld.com #[ehg-macworld1p.hitbox.com]
127.0.0.1  a.maximmag.co.uk
127.0.0.1  a.networkworld.com #[ehg-networkworld1p.hitbox.com]
127.0.0.1  a.newcars.com #[ehg-classifiedventures.hitbox.com]
127.0.0.1  ths.news.com.au
127.0.0.1  a.nvidia.com
127.0.0.1  a.nypost.com
127.0.0.1  a.oceansalive.org
127.0.0.1  a.ocregister.com
127.0.0.1  b.pcadvisor.co.uk
127.0.0.1  a.peoplepc.com
127.0.0.1  tul.pcgamer.com
127.0.0.1  hb.pcworld.com
127.0.0.1  a.playlistmag.com
127.0.0.1  webanalytics.qualcomm.com
127.0.0.1  c.realtytrac.com
127.0.0.1  a.salon.com
127.0.0.1  wss.scmagazine.com #[ehg-haymarket.hitbox.com]
127.0.0.1  a.scotsman.com
127.0.0.1  a.seenon.com
127.0.0.1  a.shutterfly.com
127.0.0.1  a.sourcemedia.com
127.0.0.1  a.stern.de
127.0.0.1  b.techworld.com
127.0.0.1  a.telegraph.co.uk
127.0.0.1  a.timesunion.com
127.0.0.1  ngd.thesun.co.uk
127.0.0.1  tgd.timesonline.co.uk
127.0.0.1  a.tiscali.co.uk
127.0.0.1  a.undoit.org
127.0.0.1  a.venetian.com
127.0.0.1  a.vonage.com
127.0.0.1  i.wynnlasvegas.com
# [WebStat.com, L.L.C]
127.0.0.1  dce.nextstat.com
127.0.0.1  bill.dce.nextstat.com
127.0.0.1  hits.nextstat.com
127.0.0.1  randy.dce.nextstat.com
127.0.0.1  hv3.webstat.com
127.0.0.1  hits.webstat.com #[McAfee.Cookie-Webstat]
# [WeDirect, Inc]
127.0.0.1  euroseek.com
127.0.0.1  www.euroseek.com
127.0.0.1  www.euroseek.net
127.0.0.1  www.ownbox.com #[Microsoft.Typo-Patrol]
127.0.0.1  usseek.com
127.0.0.1  www.usseek.com
# [Whistle Software][Panda Spyware/Whistle]
127.0.0.1  www.uslocalweather.com
127.0.0.1  www.wsel.net
127.0.0.1  www.whistlesoftware.com
# [Worldata]
127.0.0.1  webconnect.net
127.0.0.1  wexchange.webconnect.net
127.0.0.1  remote.webconnect.net
127.0.0.1  reporting.webconnect.net
127.0.0.1  secure.webconnect.net
127.0.0.1  www.webconnect.net #[SunBelt.WebConnect.net]
127.0.0.1  www.worldata.com
# [WhenUcom Inc]
127.0.0.1  a1964.g.akamai.net
127.0.0.1  www.clock-sync.com #[ADW_CLOCKSYNC.A]
127.0.0.1  www.crunchgames.com
127.0.0.1  www.crunchtoolbar.com
127.0.0.1  getweathercast.com
127.0.0.1  www.getweathercast.com #[Adware-Weathercast][Trojan.Win32.VB.fk]
127.0.0.1  www.fanzonetoolbar.com #[AdWare.Win32.SaveNow.z]
127.0.0.1  akapp.memedia.com
127.0.0.1  app.memedia.com
127.0.0.1  offers.memedia.com
127.0.0.1  web.memedia.com
127.0.0.1  www.memedia.com #[McAfee.MeMedia]
127.0.0.1  www.pbtoolbar.com #[PriceBandit Toolbar]
127.0.0.1  pricebandit.com
127.0.0.1  www.pricebandit.com #[SpySweeper.whenu.searchbar/pricebandit]
127.0.0.1  whenu.com #[Adware-WhenU][SiteAdvisor.whenu.com]
127.0.0.1  akapp.whenu.com
127.0.0.1  akdwl.whenu.com
127.0.0.1  akweb.whenu.com
127.0.0.1  app.whenu.com
127.0.0.1  bidtxt.whenu.com
127.0.0.1  chromium.whenu.com
127.0.0.1  clock.whenu.com
127.0.0.1  download.whenu.com
127.0.0.1  mercury.whenu.com
127.0.0.1  offers.whenu.com #[a1401.x.akamai.net]
127.0.0.1  spapp.whenu.com
127.0.0.1  spweather.whenu.com
127.0.0.1  spweb.whenu.com #[a1401.x.akamai.net]
127.0.0.1  tin.whenu.com
127.0.0.1  titanium.whenu.com
127.0.0.1  web.whenu.com
127.0.0.1  weather.whenu.com
127.0.0.1  zinc.whenu.com
127.0.0.1  whenushop.whenu.com
127.0.0.1  www.whenu.com #[SpySweeper.Adware.whenu]
127.0.0.1  www.whenudownloads.com
127.0.0.1  www.whenushop.com #[SiteAdvisor.whenushop.com]
127.0.0.1  www.whenu.com.edgesuite.net
127.0.0.1  whenusearch.com #[AdvWare.SaveNow.r]
127.0.0.1  www.whenusearch.com #[SiteAdvisor.whenusearch.com][a731.x.akamai.net]
# [W3i Holdings, LLC][Adware Bundler]
127.0.0.1  www.free-games-online.com
127.0.0.1  lan.free-lyrics-online.com
127.0.0.1  off.free-lyrics-online.com #[off.freeze.com]
127.0.0.1  rdt.free-lyrics-online.com
127.0.0.1  register.free-lyrics-online.com
127.0.0.1  www.free-lyrics-online.com #[Parked.redirect]
127.0.0.1  ads.freeze.com
127.0.0.1  adman.freeze.com
127.0.0.1  download.freeze.com #[Adware.Win32.Freeze.com]
127.0.0.1  download2.freeze.com #[Tenebril.Freeze.com]
127.0.0.1  img.freeze.com
127.0.0.1  lan.freeze.com
127.0.0.1  my.freeze.com #[SpywareWarrior.adw2005][a798.g.akamai.net]
127.0.0.1  off.freeze.com
127.0.0.1  pops.freeze.com #[GamHelper]
127.0.0.1  register.freeze.com
127.0.0.1  regman.freeze.com
127.0.0.1  search.freeze.com
127.0.0.1  www3.freeze.com #[SiteAdvisor.freeze.com]
127.0.0.1  www.freeze.com #[Rogue/Suspect]
127.0.0.1  www.freezecoldcash.com
127.0.0.1  www.freezemedia.com
127.0.0.1  ringtone.com #[StopBadware.org Report]
127.0.0.1  lan.ringtone.com #[lan.freeze.com]
127.0.0.1  rdt2.ringtone.com
127.0.0.1  www.ringtone.com
127.0.0.1  www.risoftsystems.com
127.0.0.1  off.screensaver.com
127.0.0.1  register.screensaver.com #[StopBadware.org Report]
127.0.0.1  rdt.screensaver.com
127.0.0.1  www.screensaver.com #[SiteAdvisor.screensaver.com][a1752.g.akamai.net]
127.0.0.1  off.wallpapers.com
127.0.0.1  www.wallpapers.com
127.0.0.1  www.wallpapervault.com
# [Wild Media, LLC][Contextual Choice Marketing]
127.0.0.1  server1.103092804.com
127.0.0.1  server2.103092804.com
127.0.0.1  server3.103092804.com
127.0.0.1  server4.103092804.com #[server2.adsrve.com]
127.0.0.1  www.103092804.com #[McAfee.Adware-IEHost]
127.0.0.1  www.ads234.com #[PcTools.Winpage Blocker]
127.0.0.1  ads345.com
127.0.0.1  www.ads345.com
127.0.0.1  adsrve.com #[App/IEDriver-A][Adware-Verticity]
127.0.0.1  ftp.adsrve.com
127.0.0.1  server1.adsrve.com
127.0.0.1  server2.adsrve.com #[eTrust.Adsrve]
127.0.0.1  server3.adsrve.com
127.0.0.1  server4.adsrve.com
127.0.0.1  www.adsrve.com #[AdWare.AdSrve.b][Adware.IEHost]
127.0.0.1  www.consumersoftwarelabs.com #[SunBelt.Malwhere]
127.0.0.1  www.contextualchoice.com
127.0.0.1  getmaxspeed.com
127.0.0.1  www.getmaxspeed.com
127.0.0.1  a1.interclick.com
127.0.0.1  campaigns.interclick.com #[campaigns.interclick.r3h.net]
127.0.0.1  www.interclick.com
127.0.0.1  origin.midaddle.com #[WinPage Affiliate][ADW_MIDADDLE.G]
127.0.0.1  www.midaddle.com #[Troj/Midaddle-C]
127.0.0.1  www.netspry.com #[McAfee.StartPage-IS][SunBelt.netspry.com]
127.0.0.1  www.spiderpilot.com
127.0.0.1  origin.statblaster.com #[Adware.StatBlaster]
127.0.0.1  turbodownload.net
127.0.0.1  www.turbodownload.net
127.0.0.1  www.playminigolf.com
127.0.0.1  www.wildarcade.com
127.0.0.1  www.yellow-sticky.com #[Troj/Midaddle-C]
# [ConsumerSoftwarelabs Group]
127.0.0.1  www.beautifulworldsavers.com
127.0.0.1  www.custommotorcyclesavers.com
127.0.0.1  www.getsafeguard.com
127.0.0.1  www.naughtynudesavers.com
127.0.0.1  www.sexybikinisavers.com
127.0.0.1  www.sexylingeriesavers.com
# [Wishbone Media]
127.0.0.1  gmail.com.org
127.0.0.1  lycos.com.org
127.0.0.1  microsoft.com.org
127.0.0.1  www.www.microsoft.com.org
127.0.0.1  orbitcycle.com
127.0.0.1  banners.orbitcycle.com
127.0.0.1  shagorgag.orbitcycle.com
127.0.0.1  www.orbitcycle.com
127.0.0.1  www.shops.com
127.0.0.1  www.trips.com
127.0.0.1  wish7.com #[SunBelt.Wish7.com]
127.0.0.1  www.wish7.com
127.0.0.1  toolbar.wishbone.com #[PcTools.Wishbone Toolbar]
127.0.0.1  your.wishbone.com
127.0.0.1  wapd.wishbone.com
127.0.0.1  www.wishbone.com
127.0.0.1  yeah.com #[SunBelt.Yeah.com]
127.0.0.1  www.yeah.com
127.0.0.1  your.com #[digimedia.com]
127.0.0.1  www.your.com
# [Wizteen Inc]
127.0.0.1  images.iconfun.com
127.0.0.1  www.iconfun.com #[SiteAdvisor.iconfun.com]
127.0.0.1  www.makeavatars.com
127.0.0.1  wizteen.com
127.0.0.1  www.wizteen.com #[AdWare.Win32.SearchIt.k]
# [The Weather Underground]
127.0.0.1  ads-aa.wunderground.com
127.0.0.1  ads3.wunderground.com
127.0.0.1  ads.wunderground.com #[SecuritySpace.WebBug]
127.0.0.1  as5000.wunderground.com
127.0.0.1  server.as5000.com
127.0.0.1  server2.as5000.com
# [Wolfgang Lanzrath]
127.0.0.1  badzeit.ivwbox.de
127.0.0.1  chiemgau.ivwbox.de
127.0.0.1  chip.ivwbox.de
127.0.0.1  ciao.ivwbox.de
127.0.0.1  digiworl.ivwbox.de
127.0.0.1  express.ivwbox.de
127.0.0.1  faz.ivwbox.de
127.0.0.1  finatime.ivwbox.de
127.0.0.1  focus.ivwbox.de #[SunBelt.ivwbox]
127.0.0.1  gamona.ivwbox.de
127.0.0.1  gmx.ivwbox.de
127.0.0.1  golem.ivwbox.de
127.0.0.1  handbl.ivwbox.de
127.0.0.1  haz.ivwbox.de
127.0.0.1  heise.ivwbox.de
127.0.0.1  heute.ivwbox.de
127.0.0.1  insideha.ivwbox.de
127.0.0.1  kabel1.ivwbox.de
127.0.0.1  ksta.ivwbox.de
127.0.0.1  lycos.ivwbox.de
127.0.0.1  maerkall.ivwbox.de
127.0.0.1  mclient.ivwbox.de
127.0.0.1  mdr.ivwbox.de
127.0.0.1  merkuron.ivwbox.de
127.0.0.1  mobile.ivwbox.de
127.0.0.1  mp3world.ivwbox.de
127.0.0.1  msn.ivwbox.de
127.0.0.1  myvideo.ivwbox.de
127.0.0.1  n24.ivwbox.de
127.0.0.1  netzeitu.ivwbox.de
127.0.0.1  newsclic.ivwbox.de
127.0.0.1  ntv.ivwbox.de
127.0.0.1  offpost.ivwbox.de
127.0.0.1  pcmagzin.ivwbox.de
127.0.0.1  pcwelt.ivwbox.de #[Ewido.TrackingCookie.Ivwbox]
127.0.0.1  pro7.ivwbox.de
127.0.0.1  qs.ivwbox.de
127.0.0.1  reuterde.ivwbox.de
127.0.0.1  rheinmai.ivwbox.de
127.0.0.1  rponl.ivwbox.de
127.0.0.1  rtl.ivwbox.de
127.0.0.1  sat1.ivwbox.de
127.0.0.1  spiegel.ivwbox.de
127.0.0.1  sport1.ivwbox.de
127.0.0.1  stern.ivwbox.de
127.0.0.1  stimme.ivwbox.de
127.0.0.1  studivz.ivwbox.de
127.0.0.1  sueddeut.ivwbox.de
127.0.0.1  swr.ivwbox.de
127.0.0.1  szon.ivwbox.de
127.0.0.1  rbb.ivwbox.de
127.0.0.1  rheinzei.ivwbox.de
127.0.0.1  tagessch.ivwbox.de
127.0.0.1  tagspieg.ivwbox.de
127.0.0.1  tecchan.ivwbox.de
127.0.0.1  teletari.ivwbox.de
127.0.0.1  tiscali.ivwbox.de #[WebBug]
127.0.0.1  toi.ivwbox.de
127.0.0.1  vanity.ivwbox.de
127.0.0.1  webdessl.ivwbox.de
127.0.0.1  welt.ivwbox.de
127.0.0.1  welten.ivwbox.de
127.0.0.1  wetter.ivwbox.de
127.0.0.1  wetteronl.ivwbox.de
127.0.0.1  wirtwoch.ivwbox.de
127.0.0.1  wissende.ivwbox.de
127.0.0.1  www.ivwbox.de
127.0.0.1  yahoo.ivwbox.de
127.0.0.1  zdf.ivwbox.de
127.0.0.1  zdnet.ivwbox.de
127.0.0.1  zeitonl.ivwbox.de
# [WURLD Media][William Boy]
127.0.0.1  www.301c.com
127.0.0.1  www.buyersport.com #[eTrust.WurldMedia.BuyersPort]
127.0.0.1  qksrv.growhope.com
127.0.0.1  www.growhope.com
127.0.0.1  urm.lxsystems.com
127.0.0.1  web.lxsystems.com
127.0.0.1  www.lxsystems.com #[Trojan.TrustedZones]
127.0.0.1  www.peerimpact.com
127.0.0.1  ins.rdxrp.com
127.0.0.1  www.rdxrp.com #[McAfee.Adware-WurldMedia]
127.0.0.1  www.wurldmedia.com #[Adware.Wurldmedia][SunBelt.Wurldmedia]
127.0.0.1  www.wurldmedia.net
# [X10 Wireless Technology]
127.0.0.1  ads.x10.com #[SpySweeper.Spy.Cookie]
127.0.0.1  contest.x10.com
127.0.0.1  control.x10.com #[SunBelt.X10.com]
127.0.0.1  ftp.x10.com
127.0.0.1  graphics.x10.com
127.0.0.1  images.x10.com
127.0.0.1  reports.x10.com
127.0.0.1  site.x10.com
127.0.0.1  software.x10.com
127.0.0.1  store.x10.com
127.0.0.1  x10-beta.com
127.0.0.1  x10.com
127.0.0.1  www.x10.com
# [Yahoo][Overture]
127.0.0.1  adinterax.com #[eTrust.Tracking.Cookie]
127.0.0.1  mi.adinterax.com
127.0.0.1  tr.adinterax.com
127.0.0.1  www.adinterax.com
127.0.0.1  pic.geocities.com
127.0.0.1  visit.geocities.com
127.0.0.1  hostingprod.com #[SecuritySpace.WebBug]
127.0.0.1  cm.cbsnews.overture.com
127.0.0.1  cm.au.thewest.overture.com
127.0.0.1  cm.de.overture.com
127.0.0.1  cm.eu.guardian.overture.com
127.0.0.1  cm.guardian.overture.com
127.0.0.1  cm.ibs.overture.com
127.0.0.1  cm.it.kataweb.overture.com
127.0.0.1  cm.ivillage.overture.com
127.0.0.1  cm.mtv.overture.com
127.0.0.1  cm.tw.overture.com #[cm.tw.g.ysm.yahoo.com]
127.0.0.1  cm.uk.independent.overture.com
127.0.0.1  cm.weather.overture.com
127.0.0.1  cmhtml.overture.com #[Content Match]
127.0.0.1  cmhtml.cbsnews.overture.com
127.0.0.1  cmhtml.de.overture.com
127.0.0.1  cmhtml.es.overture.com
127.0.0.1  cmhtml.fr.overture.com #[Panda.Spyware:Cookie/Overture]
127.0.0.1  cmhtml.ibs.overture.com #[Ewido.TrackingCookie.Overture]
127.0.0.1  cmxml.nationalgeo.overture.com
127.0.0.1  cmhtml.nl.overture.com #[SunBelt.Overture.com]
127.0.0.1  cmhtml.revenuescience.overture.com
127.0.0.1  cmhtml.uk.overture.com
127.0.0.1  cmhtml.vendare.overture.com
127.0.0.1  cmls.overture.com
127.0.0.1  cmx.tw.yahoo.overture.com
127.0.0.1  convctr.overture.com #[SiteAdvisor.crawler.com]
127.0.0.1  ctxtads.overture.com #[eTrust.Tracking.Cookie]
127.0.0.1  data2.perf.overture.com
127.0.0.1  data3.perf.overture.com #[McAfee.Cookie-Overture]
127.0.0.1  data4.perf.overture.com
127.0.0.1  data.wa.perf.overture.com
127.0.0.1  dmxml.smartname.overture.com
127.0.0.1  html.overture.com
127.0.0.1  inventory.overture.com
127.0.0.1  rc12.overture.com #[MVPS.Criteria]
127.0.0.1  rc23.overture.com #[MVPS.Criteria]
127.0.0.1  redir.overture.com #[SpySweeper.Spy.Cookie]
127.0.0.1  perf.overture.com
127.0.0.1  srv.perf.overture.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  xml.ivillage.overture.com
127.0.0.1  xml.weather.overture.com
127.0.0.1  ypn-100.overture.com
127.0.0.1  ypn-js.overture.com #[Yahoo Contextual Ads]
127.0.0.1  adserver.yahoo.com
127.0.0.1  us.adserver.yahoo.com
127.0.0.1  pn1.adserver.yahoo.com
127.0.0.1  tw2.adserver.yahoo.com
127.0.0.1  bc-beta.ads.yahoo.com
127.0.0.1  xpcs.ads.yahoo.com
127.0.0.1  advision.webevents.yahoo.com
127.0.0.1  ads.yimg.com
# [YesUp Ecommerce Solutions]
127.0.0.1  clicksor.com
127.0.0.1  ads.clicksor.com
127.0.0.1  main.clicksor.com
127.0.0.1  mci12.clicksor.com
127.0.0.1  search.clicksor.com
127.0.0.1  track.clicksor.com
127.0.0.1  www.clicksor.com
127.0.0.1  www.e-mailpromotion.com
127.0.0.1  goadbar.com
127.0.0.1  www.infinityads.com
127.0.0.1  multipops.com
127.0.0.1  service.multi-pops.com
127.0.0.1  www1.multipops.com
127.0.0.1  www2.multipops.com
127.0.0.1  www.multipops.com
127.0.0.1  gopopup.com
127.0.0.1  www.gopopup.com
127.0.0.1  paypopup.com
127.0.0.1  banner.paypopup.com
127.0.0.1  central.paypopup.com
127.0.0.1  central2.paypopup.com
127.0.0.1  creative.paypopup.com
127.0.0.1  popunder.paypopup.com
127.0.0.1  www1.paypopup.com
127.0.0.1  www2.paypopup.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www3.paypopup.com
127.0.0.1  www4.paypopup.com
127.0.0.1  www5.paypopup.com
127.0.0.1  www6.paypopup.com
127.0.0.1  www7.paypopup.com
127.0.0.1  www8.paypopup.com
127.0.0.1  www9.paypopup.com #[toolbar.cab][hotbar.com]
127.0.0.1  www10.paypopup.com
127.0.0.1  www20.paypopup.com
127.0.0.1  www21.paypopup.com #[SunBelt.PayPopup.com]
127.0.0.1  www210.paypopup.com
127.0.0.1  www211.paypopup.com
127.0.0.1  www212.paypopup.com
127.0.0.1  www213.paypopup.com
127.0.0.1  www214.paypopup.com
127.0.0.1  www215.paypopup.com
127.0.0.1  www216.paypopup.com
127.0.0.1  www217.paypopup.com
127.0.0.1  www218.paypopup.com
127.0.0.1  www219.paypopup.com
127.0.0.1  www220.paypopup.com
127.0.0.1  www221.paypopup.com
127.0.0.1  www.paypopup.com #[eTrust.Tracking.Cookie]
127.0.0.1  popinads.com
127.0.0.1  www.popinads.com
127.0.0.1  www.xxxwebtraffic.com
127.0.0.1  yesadvertising.com
127.0.0.1  test.yesadvertising.com
127.0.0.1  www1.yesadvertising.com
127.0.0.1  www2.yesadvertising.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  www3.yesadvertising.com
127.0.0.1  www4.yesadvertising.com
127.0.0.1  www5.yesadvertising.com
127.0.0.1  www6.yesadvertising.com
127.0.0.1  www7.yesadvertising.com
127.0.0.1  www8.yesadvertising.com
127.0.0.1  www9.yesadvertising.com
127.0.0.1  www10.yesadvertising.com
127.0.0.1  www11.yesadvertising.com
127.0.0.1  www12.yesadvertising.com
127.0.0.1  www13.yesadvertising.com
127.0.0.1  www14.yesadvertising.com
127.0.0.1  www15.yesadvertising.com
127.0.0.1  www215.yesadvertising.com
127.0.0.1  www216.yesadvertising.com
127.0.0.1  www217.yesadvertising.com
127.0.0.1  www218.yesadvertising.com
127.0.0.1  www219.yesadvertising.com
127.0.0.1  www220.yesadvertising.com
127.0.0.1  www221.yesadvertising.com
127.0.0.1  yesup.com
127.0.0.1  bt.yesup.com
127.0.0.1  reseller.yesup.com
127.0.0.1  us.yesup.com
127.0.0.1  www2.yesup.com
127.0.0.1  www.yesup.com
127.0.0.1  forum.yesup.net
127.0.0.1  www.yesup.net
127.0.0.1  whyppc.com #[SunBelt.WhyPPC]
127.0.0.1  www.whyppc.com #[Parasite.Pugi]
127.0.0.1  yourstats.net
127.0.0.1  www.yourstats.net
# [YFDirect Inc][Netblue]
127.0.0.1  www.everyfreegift.com #[SiteAdvisor.everyfreegift.com]
127.0.0.1  ap.net-blue.net
# [ZapSpot, Inc]
127.0.0.1  www.p3marketing.com
127.0.0.1  download.zapspot.com #[SiteAdvisor.zapspot]
127.0.0.1  www.zapspot.com #[eTrust.ZapSpot]
# [ZEDO][Tracking Service]
127.0.0.1  zedo.com #[SecuritySpace.WebBug]
127.0.0.1  ads.zedo.com #[McAfee.Cookie-Zedo]
127.0.0.1  c1.zedo.com #[a1979.g.akamai.net]
127.0.0.1  c2.zedo.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c3.zedo.com
127.0.0.1  c4.zedo.com #[zedo.vo.llnwd.net]
127.0.0.1  c5.zedo.com
127.0.0.1  c6.zedo.com
127.0.0.1  c7.zedo.com
127.0.0.1  c8.zedo.com #[zedo.vo.llnwd.net]
127.0.0.1  freeze.zedo.com
127.0.0.1  g.zedo.com #[zedo.live365.com]
127.0.0.1  gw.zedo.com
127.0.0.1  l1.zedo.com #[a1101.g.akamai.net]
127.0.0.1  l2.zedo.com
127.0.0.1  l3.zedo.com
127.0.0.1  l4.zedo.com #[Panda.Spyware:Cookie/Zedo]
127.0.0.1  l5.zedo.com
127.0.0.1  l6.zedo.com #[a515.g.akamai.net][Tenebril.Tracking.Cookie]
127.0.0.1  l7.zedo.com
127.0.0.1  l8.zedo.com
127.0.0.1  simg.zedo.com #[zedo.vo.llnwd.net][a556.g.akamai.net]
127.0.0.1  ss1.zedo.com
127.0.0.1  ss2.zedo.com
127.0.0.1  xads.zedo.com
127.0.0.1  yads.zedo.com
127.0.0.1  www.zedo.com #[Adware.RaxSearch]
# [Innovative Marketing Group][NSCACHE.NET][SetupAHost]
127.0.0.1  adnetserver.com
127.0.0.1  www.adnetserver.com
127.0.0.1  advancedcleaner.com #[Symantec.AdvancedCleaner]
127.0.0.1  secure.advancedcleaner.com
127.0.0.1  www.advancedcleaner.com
127.0.0.1  adserver.affiliatemg.com
127.0.0.1  amaena.com
127.0.0.1  www.amaena.com #[Trojan.TrustedZone]
127.0.0.1  www.amxtravel.com
127.0.0.1  antiworm2008.com #[SunBelt.Antiworm2008]
127.0.0.1  hit.antiworm2008.com
127.0.0.1  sale.antiworm2008.com
127.0.0.1  www.antiworm2008.com
127.0.0.1  www.antivirus-comparison.com
127.0.0.1  www.antivirusproshop.com
127.0.0.1  ads2desk.com
127.0.0.1  www.bestofonlinesearch.com
127.0.0.1  www.bestsearchnet.com
127.0.0.1  betbonus.com
127.0.0.1  www.betbonus.com
127.0.0.1  www.billingcomplete.com
127.0.0.1  billingnow.com #[Trojan.TrustedZone]
127.0.0.1  secure.billingnow.com
127.0.0.1  www.billingnow.com
127.0.0.1  stats.bookmyfares.com
127.0.0.1  www.bookmyfares.com
127.0.0.1  www.cannis.org
127.0.0.1  www.casinoaceking.com
127.0.0.1  www.clickwwwsearch.com
127.0.0.1  www.completebilling.com
127.0.0.1  www.computershield.com
127.0.0.1  locator.contentsvc.com
127.0.0.1  www.creditsecretguide.com
127.0.0.1  dctrick.com
127.0.0.1  cl.dctrick.com
127.0.0.1  cdn.downloadcontrol.com #[setuphost.vo.llnwd.net][Win32/Adware.WinFixer]
127.0.0.1  drivecleaner.com #[McAfee.FakeAlert-I]
127.0.0.1  cdn.drivecleaner.com
127.0.0.1  dynamique.drivecleaner.com
127.0.0.1  freeware.updates.drivecleaner.com
127.0.0.1  go.drivecleaner.com #[eTrust.Win32/Beenut]
127.0.0.1  jsp.drivecleaner.com
127.0.0.1  secure.drivecleaner.com
127.0.0.1  stats.drivecleaner.com
127.0.0.1  www.drivecleaner.com #[Symantec.DriveCleaner]
127.0.0.1  www.driveprotector.com
127.0.0.1  www.enhanceyourbust.com
127.0.0.1  www.epinioncash.com
127.0.0.1  errorpatrol.com
127.0.0.1  secure.errorpatrol.com
127.0.0.1  stats.errorpatrol.com
127.0.0.1  www.errorpatrol.com
127.0.0.1  errorprotector.com #[SunBelt.ErrorProtector][secure.winsoftware.com]
127.0.0.1  bin.errorprotector.com #[Downloader.Win32.WinFixer.l]
127.0.0.1  go.errorprotector.com #[Google Warning]
127.0.0.1  report.errorprotector.com
127.0.0.1  www.errorprotector.com #[HJTH.Downloader.Agent]
127.0.0.1  errorsafe.com #[Downloader.Win32.Agent.d]
127.0.0.1  br.errorsafe.com
127.0.0.1  de.errorsafe.com
127.0.0.1  download.errorsafe.com #[Prevx.Rogue.ErrorSafe]
127.0.0.1  go.errorsafe.com
127.0.0.1  kb.errorsafe.com
127.0.0.1  nl.errorsafe.com
127.0.0.1  se.errorsafe.com #[SiteAdvisor.errorsafe.com]
127.0.0.1  secure.errorsafe.com
127.0.0.1  utils.errorsafe.com #[winfixer.com]
127.0.0.1  www.errorsafe.com #[Symantec.ErrorSafe]
127.0.0.1  www.ezmp3downloads.com
127.0.0.1  www.fileprotector.com
127.0.0.1  genericscanner.com #[Rogue/Suspect]
127.0.0.1  www.genericscanner.com
127.0.0.1  getfreecar.com
127.0.0.1  www.getfreecar.com
127.0.0.1  goldenantispy.com
127.0.0.1  rescue.goldenantispy.com
127.0.0.1  sale.goldenantispy.com
127.0.0.1  www.goldenantispy.com
127.0.0.1  gomyron.com #[Malicious Links]
127.0.0.1  jsp.gomyron.com
127.0.0.1  members.us.homecs.com
127.0.0.1  www.homecs.com #[ripoffreport.com]
127.0.0.1  locator.imagesrvr.com
127.0.0.1  locator1.cdn.imagesrvr.com #[setuphost.vo.llnwd.net]
127.0.0.1  www.incrediseek.com
127.0.0.1  innovativemarketing.com #[Trojan.Vundo.B][TROJ_CRYPT.N]
127.0.0.1  www.innovativemarketing.com
127.0.0.1  internetantispy.com #[Rogue/Suspect]
127.0.0.1  www.internetantispy.com
127.0.0.1  www.jobdrill.com
127.0.0.1  www.kpremium.com
127.0.0.1  setuphost.vo.llnwd.net
127.0.0.1  www.matchservice.com
127.0.0.1  www.maxkb.com
127.0.0.1  www.mcafeereview.com #[locator.imagesrvr.com]
127.0.0.1  mp3u.com
127.0.0.1  download.mp3u.com
127.0.0.1  www.mp3u.com
127.0.0.1  www.mp3asap.com
127.0.0.1  www.mp3asap.net
127.0.0.1  www.multimediafixer.com
127.0.0.1  www.mysurvey4u.com
127.0.0.1  www.nortoncomparison.com
127.0.0.1  content.onerateld.com #[setuphost.vo.llnwd.net]
127.0.0.1  www.onestoponlineshop.net
127.0.0.1  onlinepcguard.com
127.0.0.1  sale.onlinepcguard.com
127.0.0.1  www.onlinepcguard.com
127.0.0.1  www.pcsupercharger.com
127.0.0.1  pcturbopro.com
127.0.0.1  www.pcturbopro.com
127.0.0.1  popupavenger.com
127.0.0.1  www.popupavenger.com
127.0.0.1  images.popupguard.com
127.0.0.1  www.popupguard.com
127.0.0.1  software.protectdownloads.com #[setuphost.vo.llnwd.net]
127.0.0.1  stats1.reliablestats.com #[TR/Dldr.FakeAv.C]
127.0.0.1  stats2.reliablestats.com
127.0.0.1  www.review-software.com
127.0.0.1  www.ringtonegold.com #[LURHQ.IFrame.Exploit]
127.0.0.1  search42.com
127.0.0.1  www.search42.com
127.0.0.1  www.searchfindsearch.com
127.0.0.1  setupahost.net
127.0.0.1  noc.setupahost.net
127.0.0.1  rr-grp1.yyz1.cl1.setupahost.net
127.0.0.1  www.setupahost.net
127.0.0.1  www.sexbuddies.com
127.0.0.1  sexprofit.com
127.0.0.1  go.sexprofit.com
127.0.0.1  jsp.sexprofit.com
127.0.0.1  sxp.sexprofit.com
127.0.0.1  www.sexprofit.com
127.0.0.1  www.smax.us #[Innovative Marketing Ukraine]
127.0.0.1  smileydistrict.com
127.0.0.1  softwareprofit.com
127.0.0.1  go.softwareprofit.com
127.0.0.1  www.softwareprofit.com
127.0.0.1  www.symantecreview.com
127.0.0.1  sysprotect.com
127.0.0.1  download.sysprotect.com
127.0.0.1  scanner.sysprotect.com
127.0.0.1  utils.sysprotect.com
127.0.0.1  www.sysprotect.com #[McAfee.SysProtect]
127.0.0.1  systemdoctor.com #[HJTH.Downloader.Agent]
127.0.0.1  de.systemdoctor.com
127.0.0.1  download.systemdoctor.com #[Win32/Adware.WinFixer]
127.0.0.1  es.systemdoctor.com
127.0.0.1  fr.systemdoctor.com
127.0.0.1  go.systemdoctor.com #[Symantec.SystemDoctor]
127.0.0.1  instlog.systemdoctor.com
127.0.0.1  px.systemdoctor.com
127.0.0.1  www.systemdoctor.com #[Downloader.Win32.WinFixer.l]
127.0.0.1  www.tattoobitches.com
127.0.0.1  www.theringtonesource.com
127.0.0.1  vantagesoftware.com #[Rogue/Suspect]
127.0.0.1  billing.vantagesoftware.com
127.0.0.1  www.vantagesoftware.com #[SiteAdvisor.vantagesoftware.com]
127.0.0.1  www.viptravelagent.com
127.0.0.1  viragehosting.com
127.0.0.1  www.virusguard.com
127.0.0.1  virussoftwarereview.com
127.0.0.1  purchase.virussoftwarereview.com
127.0.0.1  www.virussoftwarereview.com
127.0.0.1  www.virussw.com
127.0.0.1  http.edge.vru4.com #[McAfee.Adware-Apropos]
127.0.0.1  www.wantprofit.com
127.0.0.1  www.webinvestigator.com
127.0.0.1  go.winadblocker.com
127.0.0.1  secure.winadblocker.com
127.0.0.1  www.winadblocker.com
127.0.0.1  secure.winantispam.com
127.0.0.1  www.winantispam.com
127.0.0.1  secure.winantispy.com
127.0.0.1  www.winantispy.com
127.0.0.1  winantivirus.com #[Google Warning]
127.0.0.1  br.winantivirus.com
127.0.0.1  de.winantivirus.com
127.0.0.1  es.winantivirus.com
127.0.0.1  fr.winantivirus.com
127.0.0.1  go.winantivirus.com #[Trojan.Virantix]
127.0.0.1  kb.winantivirus.com
127.0.0.1  hk.winantivirus.com
127.0.0.1  instlog.winantivirus.com
127.0.0.1  purchase.winantivirus.com
127.0.0.1  secure.winantivirus.com #[SiteAdvisor.winantivirus.com]
127.0.0.1  support.winantivirus.com
127.0.0.1  ulog.winantivirus.com
127.0.0.1  utils.winantivirus.com
127.0.0.1  www.winantivirus.com #[Rogue/Suspect][TR/Dldr.FakeAV.A.6]
127.0.0.1  winantivirus.co.uk
127.0.0.1  www.winantivirus.co.uk
127.0.0.1  www.win-anti-virus-pro.com
127.0.0.1  www.win-virus-pro.com
127.0.0.1  winantispyware.com #[Symantec.WinAntiSpyware]
127.0.0.1  download.winantispyware.com
127.0.0.1  go.winantispyware.com #[SiteAdvisor.winantispyware.com]
127.0.0.1  www.winantispyware.com #[Rogue/Suspect]
127.0.0.1  kb.winantiviruspro.com
127.0.0.1  www.winantiviruspro.com #[SpySweeper.Spy.Cookie]
127.0.0.1  wincontentfilter.com
127.0.0.1  download.wincontentfilter.com
127.0.0.1  secure.wincontentfilter.com
127.0.0.1  download.windrivecleaner.com
127.0.0.1  www.windrivecleaner.com
127.0.0.1  www.windrivesafe.com
127.0.0.1  winfirewall.com
127.0.0.1  www.winfirewall.com
127.0.0.1  winfixer.co.uk
127.0.0.1  br.winfixer.com #[SiteAdvisor.winfixer.com]
127.0.0.1  download.winfixer.com #[Symantec.WinFixer]
127.0.0.1  fr.winfixer.com
127.0.0.1  winnanny.com #[Trojan.TrustedZone]
127.0.0.1  www.winnanny.com
127.0.0.1  www.winpluspak.com
127.0.0.1  ls.winpopupguard.com
127.0.0.1  www.winpopupguard.com
127.0.0.1  winprivacyguard.com
127.0.0.1  www.winprivacyguard.com
127.0.0.1  www.winproductions.com
127.0.0.1  activate.winsoftware.com
127.0.0.1  download.cdn.winsoftware.com #[setuphost.vo.llnwd.net][Win32/Adware.WinFixer]
127.0.0.1  updates.winsoftware.com
127.0.0.1  secure.winsoftware.com
127.0.0.1  trial.updates.winsoftware.com
127.0.0.1  www.winsoftware.com
127.0.0.1  uk.workhomecenter.com
127.0.0.1  www.workhomecenter.com
# [Mindset Interactive][Vista Interactive][BroadSpring Inc]
127.0.0.1  www.asn.com
127.0.0.1  www.broadnetsoftware.com
127.0.0.1  www.broadspring.com
127.0.0.1  www.flashgamejunkie.com
127.0.0.1  www.flyordie.com #[Microsoft VM]
127.0.0.1  www.idealgamebar.com
127.0.0.1  www.idealringtones.com
127.0.0.1  www.idealshopperrewards.com
127.0.0.1  www.igamebar.com
127.0.0.1  instafinder.com #[Adware.InstaFinder]
127.0.0.1  ww2.instafinder.com #[Parasite.MegaSearch]
127.0.0.1  www.instafinder.com #[ADW_INSTAFIND.B]
127.0.0.1  www.mindsetinteractive.com
127.0.0.1  www.netpalgames.com
127.0.0.1  searchenginebar.com #[Parasite.RXToolbar]
127.0.0.1  www.searchenginebar.com #[Adware.RXToolbar]
127.0.0.1  www.ileadmedia.com
# [NicTech Networks Group]
127.0.0.1  www.angrycentral.com #[server down?]
127.0.0.1  a-d-w-a-r-e.com #[Troj/Dloader-IG]
127.0.0.1  www.a-d-w-a-r-e.com
127.0.0.1  ad-w-a-r-e.com #[Win32.Canbede][Troj/Dloader-IG]
127.0.0.1  www.ad-w-a-r-e.com #[AdWare.Win32.Look2Me.ab]
127.0.0.1  kudd.com #[SiteAdvisor.kudd.com][server down?]
127.0.0.1  www.kudd.com
127.0.0.1  www.loadingwebsite.com #[server down?]
127.0.0.1  www.look2me1.com #[Spyware.Look2Me]
# [Odysseus Marketing][Spyware.ClientMan]
127.0.0.1  kazanon.com #[eTrust.Kazanon]
127.0.0.1  www.kazanon.com
127.0.0.1  odysseusmarketing.com
127.0.0.1  www.odysseusmarketing.com #[CActSetupObj Object]
127.0.0.1  spywarehelp.net #[Internet Enhancement Pak]
127.0.0.1  www.spywarehelp.net
# [Direct Revenue][Thinking Media LP][ABI Network]
127.0.0.1  abetterinternet.com #[Downloader.Stubby.A][Adware.Aurora]
127.0.0.1  download.abetterinternet.com #[Adware.StopPopupAdsNow]
127.0.0.1  st.abetterinternet.com
127.0.0.1  static.abetterinternet.com
127.0.0.1  thinstall.abetterinternet.com
127.0.0.1  www.abetterinternet.com #[Trojan-Downloader.Win32.Stubby.d]
127.0.0.1  affiliate-optimizer.com
127.0.0.1  bestoffersnetworks.com
127.0.0.1  admin.bestoffersnetworks.com
127.0.0.1  download.bestoffersnetworks.com #[SiteAdvisor.bestoffersnetworks.com]
127.0.0.1  install.bestoffersnetworks.com
127.0.0.1  s.bestoffersnetworks.com
127.0.0.1  shop.bestoffersnetworks.com #[bestoffers.activeshopper.com]
127.0.0.1  uk.shop.bestoffersnetworks.com
127.0.0.1  shopdata.bestoffersnetworks.com #[data2.activeshopper.com]
127.0.0.1  st.bestoffersnetworks.com #[SpySweeper.directrevenue-abetterinternet]
127.0.0.1  static.bestoffersnetworks.com
127.0.0.1  thinstall.bestoffersnetworks.com
# 127.0.0.1  uninstall.bestoffersnetworks.com #[disabled to allow uninstall]
# 127.0.0.1  www.bestoffersnetworks.com #[TROJ_NAIL.A][disabled to allow uninstall]
127.0.0.1  bestoffersnetworks.info
127.0.0.1  btgrab.com #[Transponder.BTGrab][Adware.Tbon]
127.0.0.1  btg.btgrab.com #[McAfee.Adware-BestOffers]
127.0.0.1  static.callinghome.biz #[Downloader-KL][Adware.Binet.DL]
127.0.0.1  corr.conscorr.com #[SunBelt.ConsCorr]
127.0.0.1  www.conscorr.com #[TrojanDownloader.stubby.c]
127.0.0.1  www.cpvmarket.com #[server down?]
127.0.0.1  www.dr-addremove.com
127.0.0.1  dr-customersupport.com
127.0.0.1  www.direct-revenue.com
127.0.0.1  www.dlmax.biz #[ADW_DLMAX.A]
127.0.0.1  aid.farmmext.com #[TSPY_DLOADER.DH]
127.0.0.1  www.farmmext.com #[eTrust.Farmmext]
127.0.0.1  install.funscreenz.com #[SiteAdvisor.funscreenz.com]
127.0.0.1  www.funscreenz.com
127.0.0.1  grandstreetinteractive.com #[Parasite.GrandStreet]
127.0.0.1  sysupdate.grandstreetinteractive.com #[Win32.Imiserv]
127.0.0.1  www.grandstreetinteractive.com #[TROJ_IMISERV.C]
127.0.0.1  localnrd.com #[ADW_NRD.A]
127.0.0.1  www.localnrd.com #[VX2.LocalNRD]
127.0.0.1  multimpp.com #[MultimppObj Class][AdvWare.BiSpy.o]
127.0.0.1  www.multimpp.com
# 127.0.0.1  www.mypctuneup.com #[disabled to allow uninstall]
127.0.0.1  master.mx-targeting.com #[Adware.MXTarget.B]
127.0.0.1  www.mx-targeting.com #[Adware.MXTarget]
127.0.0.1  as2.offeroptimizer.com
127.0.0.1  reports.offeroptimizer.com
127.0.0.1  search.offeroptimizer.com
127.0.0.1  xads.offeroptimizer.com #[PcTools.Transponder.Bolger][server down?]
127.0.0.1  ximages.offeroptimizer.com
127.0.0.1  xlime.offeroptimizer.com
127.0.0.1  xmat.offeroptimizer.com
127.0.0.1  www.offeroptimizer.com #[PcTools.Transponder.KZ515]
127.0.0.1  www.pynix.com
127.0.0.1  www.searchbasket.com #[ShopNav]
127.0.0.1  www.searchrabbit.com
127.0.0.1  www.smileysource.com
127.0.0.1  www.sohodigital.net #[Parasite.Transponder]
127.0.0.1  www.sohoint.net
127.0.0.1  supremetoolbar.com
127.0.0.1  www.supremetoolbar.com
127.0.0.1  collect.tps108.org #[PcTools.Transponder.TPS108]
127.0.0.1  server4.tps108.org
127.0.0.1  www.tps108.org #[Parasite.Transponder]
127.0.0.1  www.twain-tech.com #[Adware.Twaintec]
# [Direct Revenue Affiliates]
127.0.0.1  marchingants.com
127.0.0.1  olgaslepak.com
#
# [Various Adult Dialers]
127.0.0.1  www.1987324.com #[McAfee.Downloader-AVT]
127.0.0.1  www.69adult.tv #[Win32/Dialer.HZ]
127.0.0.1  99culi.com
127.0.0.1  www.99culi.com #[Win32/Dialer.HZ]
# [A]
127.0.0.1  www.accessoveloce.com #[HJTH.Svezia Dialer]
127.0.0.1  www.accerispartners.com #[[Dialer.Paydial]
127.0.0.1  www.accesoplugin.com #[PremiumHTML Dialer]
127.0.0.1  aconti.net
127.0.0.1  www.aconti.net #[Dialer.Aconti]
127.0.0.1  allcontents.biz #[Trojan.Win32.Dialer.hz]
127.0.0.1  www.allcontents.biz
127.0.0.1  www.amp69.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  www.appunti-tesine.net #[Trojan.Win32.Dialer.hh]
127.0.0.1  archiviosesso.com
127.0.0.1  www.archiviosesso.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  assatanate.com
127.0.0.1  www.assatanate.com #[Win32/Dialer.QI]
127.0.0.1  at-web.co.in #[yourfreevids.com]
# [B]
127.0.0.1  www.barzellette.tv #[Win32/Dialer.HZ]
127.0.0.1  bellepoppe.com
127.0.0.1  www.bellepoppe.com #[HJTH.Trojan.Dialer.hz]
127.0.0.1  www.bocata.net #[HJTH.Marcador]
127.0.0.1  www.bocchinimania.com #[Trojan.Win32.Dialer.qi]
127.0.0.1  nl.browserupdate.co.uk
127.0.0.1  www.browserupdate.co.uk #[Browserupdate Dialer]
# [C]
127.0.0.1  adserver.cams.com
127.0.0.1  banners.cams.com #[banners.adultfriendfinder.com]
127.0.0.1  promo.cams.com
127.0.0.1  www.cbit-solutions.com
127.0.0.1  www.celebritaemodelle.com #[Win32/Dialer.HZ]
127.0.0.1  www.cercoporno.com #[Win32/Dialer.HZ]
127.0.0.1  cliphunter.com
127.0.0.1  www.cliphunter.com #[HJTH.Adult Content Dialer]
127.0.0.1  www.comeonsex.com
127.0.0.1  content-loader.com
127.0.0.1  www.content-loader.com #[SunBelt.Dialer.CCAccess][Win32/Dialer.KS]
127.0.0.1  www.czech-teens.com #[Panda Dialer.WE]
127.0.0.1  d.crackedearth.com #[Parasite.CrackedEarth]
127.0.0.1  www.crackedearth.com #[SPYW_SRCHHOOK.A]
# [D]
127.0.0.1  www.date.se #[SMS Dialer][Date Regon]
127.0.0.1  www.dialerfactory.com
127.0.0.1  preview.dialer411.com
127.0.0.1  dialxs.nl #[HJTH.DialXS][DialXSCtl Object]
127.0.0.1  dialxs.com #[DIAL_DIALXS.A]
127.0.0.1  adv.digieros.it
127.0.0.1  w3.dinerotica.com
127.0.0.1  www.dinerotica.com #[HJTH.Adult Content Dialer]
127.0.0.1  www.dikai.com #[HJTH.Adult Content Dialer]
# [E]
127.0.0.1  www.eingang69.de #[SiteAdvisor.eingang69.de]
127.0.0.1  www.eops.de #[Parasite.XDiver]
127.0.0.1  www.erostorie.com #[SiteAdvisor.erostorie.com]
127.0.0.1  www.erostars.de #[Dialer.Erostars]
127.0.0.1  www.eroticdialer.com #[Trojan.Win32.Toras]
127.0.0.1  plugin.euro-infomedia.com #[EuroInfoMedia Dialer]
# [F]
127.0.0.1  faccesborrate.com #[SiteAdvisor.faccesborrate.com]
127.0.0.1  www.faccesborrate.com
127.0.0.1  a0e6.ffx23wl.nl #[ConnectSwitch Dialer Variant]
127.0.0.1  www.filminiporno.net #[Win32/Dialer.HZ]
127.0.0.1  www.filmy.porno.pl #[Dialer.Connect]
127.0.0.1  fragolapiccante.com #[Win32/Dialer.HZ]
127.0.0.1  www.fragolapiccante.com
127.0.0.1  acxd.freeload.cc #[HJTH.DialerCenter Dialer]
127.0.0.1  www.freexvideo.net #[NOD32.Win32/Dialer.HZ]
# [G]
127.0.0.1  www.gagne-un-max.com #[WWWInstall Class][Edipole Dialer]
127.0.0.1  www.gamatgp.com #[HJTH.Adult Content Dialer]
127.0.0.1  www.giovanifichette.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  global-netcom.de #[Parasite.GlobalNetcom][Wildcard DNS]
127.0.0.1  install.global-netcom.de #[IELoaderCtl Class]
127.0.0.1  software.global-netcom.de
127.0.0.1  www.global-netcom.de #[Dialer.Coder]
127.0.0.1  secure.goodthinxx.com
127.0.0.1  www.gxplugin.com #[HJTH.Adult Content Dialer]
# [H]
127.0.0.1  hard-core-xxx.com
127.0.0.1  adult.hard-core-xxx.com
127.0.0.1  lsex.hard-core-xxx.com
127.0.0.1  osex.hard-core-xxx.com #[Porn-Dialer.Win32.Agent.aj]
127.0.0.1  filmati-porno.hardsu.net #[NOD32.Win32/Dialer.HZ]
127.0.0.1  humorcash.nl
127.0.0.1  www.humorcash.nl
# [I]
127.0.0.1  www.ilpolliceverde.net #[Trojan.Win32.Dialer.hh]
127.0.0.1  www.infodialer3000.com #[HJTH.nfoDialer3000]
127.0.0.1  deposito.instantdoor.com #[Win32/Diamin.NAF]
127.0.0.1  flat.instantdoor.com
127.0.0.1  www.italiahard.it #[NOD32.Win32/Dialer.HZ]
# [L]
127.0.0.1  libereco.net
127.0.0.1  www.libereco.net #[Parasite.OnlineDialer]
127.0.0.1  livecams.nl
127.0.0.1  www.livecams.nl #[Dialer.LiveCams]
127.0.0.1  sexvideo.lussuria.org #[JS/Exploit.ObjCode.I]
# [M]
127.0.0.1  www.manga-erotico.com #[Rubuskizo Dialer]
127.0.0.1  acceso.masminutos.com #[HJTH.Marcador]
127.0.0.1  masterdialer.de #[Parasite.MasterDialer]
127.0.0.1  www.masterdialer.de
127.0.0.1  www.mediaswitch.nl #[Win32/Trojan.Downloader.VB.FH]
127.0.0.1  dialer.medianed.nl #[HJTH.Tintel Dialer]
127.0.0.1  www.milunuda.com #[Google Warning]
127.0.0.1  www.mispoglio.com #[SiteAdvisor.mispoglio.com]
127.0.0.1  www.mistersesso.com #[Win32/Dialer.HZ]
127.0.0.1  mygalleries.biz #[SiteAdvisor.mygalleries.biz]
127.0.0.1  www.mygalleries.biz #[Win32/Dialer.HZ]
# [N]
127.0.0.1  nerisuperdotati.com
127.0.0.1  www.nerisuperdotati.com #[Win32/Dialer.HZ]
# [O]
127.0.0.1  www.otherchance.com #[Dial/Chivio-AN][Trojan.TrustedZone]
127.0.0.1  orgeamatoriali.com
127.0.0.1  www.orgeamatoriali.com #[Win32/Dialer.HZ]
# [P]
127.0.0.1  www.playitalia.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  www.pornoitalia.it #[NOD32.Win32/Dialer.HZ]
127.0.0.1  www.pornoitalianogratis.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  stream.pussyharem.com
127.0.0.1  www.pussyharem.com #[HJTH.Adult Content Dialer]
# [R]
127.0.0.1  www.ragazze-webcam.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  realarea.biz
127.0.0.1  www.realarea.biz #[Trojan.TrustedZones][HJTH.Adult Content Dialer]
127.0.0.1  www.riservatezze.com #[Win32/Dialer.HZ]
# [S]
127.0.0.1  sadomasogratuito.com #[TR/Agent.3024]
127.0.0.1  www.sadomasogratuito.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  satirika.com #[HTML/Exploit.CodeBaseExec]
127.0.0.1  www.satirika.com #[Win32/Dialer.HZ][Google Warning]
127.0.0.1  go.securecasting.com #[DIAL_EXDIAL.A]
127.0.0.1  segretarieporche.com
127.0.0.1  www.segretarieporche.com #[HJTH.Adult Content Dialer]
127.0.0.1  www.sesso1.net #[Google Warning]
127.0.0.1  www.sexfiles.nu #[SMS Dialer][Date Regon]
127.0.0.1  www.sexlinksnow.com #[HJTH.Adult Content Dialer]
127.0.0.1  www.sexop.tv #[SinCity Dialer]
127.0.0.1  sfonditalia.biz #[Trojan.TrustedZones]
127.0.0.1  www.sfonditalia.biz #[Dialer.Sfonditalia][Trojan.Win32.Dialer.hz]
127.0.0.1  www.sfondimania.net #[Win32/Dialer.HZ]
127.0.0.1  sgrunt.biz #[Dialer.Yeaknet][Trojan.TrustedZones]
127.0.0.1  www.sgrunt.biz #[DIAL_SGRUNT.A][Troj/QLowZon-E]
127.0.0.1  01.sharedsource.org
127.0.0.1  03.sharedsource.org #[UDConnect Class]
127.0.0.1  05.sharedsource.org #[HJTH.Triacom Soluciones Dialer]
127.0.0.1  09.sharedsource.org
127.0.0.1  17.sharedsource.org
127.0.0.1  18.sharedsource.org #[SunBelt.SharedSource.org]
127.0.0.1  19.sharedsource.org
127.0.0.1  20.sharedsource.org
127.0.0.1  22.sharedsource.org
127.0.0.1  www.sharedsource.org
127.0.0.1  www.solonelculo.com #[Win32/Dialer.HZ]
127.0.0.1  www.storage-tasp.com #[HJTH.Virgilio Dialer]
127.0.0.1  www.studentessetroie.com #[Trojan.Win32.Dialer.Jw]
# [T]
127.0.0.1  www.temisvolti.info #[Trojan.Win32.Dialer.hh]
127.0.0.1  camz.tintel.nl #[HJTH.Tintel Dialer]
127.0.0.1  hpintermedia.tintel.nl #[HJTH.Tintel Dialer]
127.0.0.1  xenium.tintel.nl #[HJTH.Tintel Dialer]
127.0.0.1  www.topsesso69.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  dialer.tranent.nl
127.0.0.1  pay.tranent.nl
127.0.0.1  www.tuttoagratis.com #[Trojan.Win32.Dialer.hh]
# [V]
127.0.0.1  videofree.biz
127.0.0.1  www.videofree.biz #[Win32/Dialer.HZ]
127.0.0.1  www.videohard.org #[Trojan.Win32.Dialer.on]
127.0.0.1  www.video-porno.cc #[Trojan.Win32.Dialer.hh]
# [W]
127.0.0.1  www.worldxchange.com #[Dialer.Paydial]
# [X]
127.0.0.1  neorsoft.xost.ru #[Javascript.Exploit]
127.0.0.1  www.xtraf.biz
# [Y]
127.0.0.1  yeak.net #[Dialer.Yeaknet]
127.0.0.1  www.yeak.net #[Trojan.TrustedZones]
127.0.0.1  www.world-dialer.net #[W32/Dialer.gen]
# [Z]
127.0.0.1  www.zoccoleamatoriali.com #[Win32/Dialer.HZ]
127.0.0.1  www.zoo-****.net #[Win32/Dialer.E]
# [Carima Enterprises Group]
127.0.0.1  www.celebritaspoglie.net
127.0.0.1  www.desktoplife.net #[HJTH.Trojan.Downloader.Small]
127.0.0.1  deposito.hostance.net #[Trojan.Win32.Diamin.t]
127.0.0.1  netvision.hostance.net
127.0.0.1  trk.hostance.net
127.0.0.1  deposito.traffic-advance.net #[Win32/Diamin]
127.0.0.1  flat.trafficadvance.net #[Dialer.Trafficadvance]
127.0.0.1  netvision.traffic-advance.net #[Wildcard DNS]
127.0.0.1  pv.trafficadvance.net
127.0.0.1  stat.trafficadvance.net #[Trojan.Win32.Dialer.q]
127.0.0.1  www.trafficadvance.net #[SunBelt.TrafficAdvance]
127.0.0.1  deposito.trafficredlight.net #[Win32/Diamin]
127.0.0.1  flat.trafficredlight.net
# [Carpediem Group][Wildcard DNS]
127.0.0.1  adsl.carpediem.fr #[DIAL_FEMME.A]
127.0.0.1  dialup.carpediem.fr #[HJTH.AccessMembre]
127.0.0.1  faq.carpediem.fr
127.0.0.1  kit.carpediem.fr #[SiteAdvisor.parisvoyeur.com]
127.0.0.1  10661.kit.carpediem.fr
127.0.0.1  11731.kit.carpediem.fr #[Win32/Dialer.CDDial]
127.0.0.1  16643.kit.carpediem.fr #[HJTH.Carpediem Dialer]
127.0.0.1  live.carpediem.fr
127.0.0.1  live-2.carpediem.fr
127.0.0.1  lsda.carpediem.fr
127.0.0.1  media.carpediem.fr
127.0.0.1  media2.carpediem.fr
127.0.0.1  polyfolie.carpediem.fr
127.0.0.1  public.carpediem.fr
127.0.0.1  secure.carpediem.fr
127.0.0.1  stats.carpediem.fr
127.0.0.1  support.carpediem.fr
127.0.0.1  www.carpediem.fr
127.0.0.1  www.dingophone.com
127.0.0.1  dialer.eurodialer.com #[Win32/TrojanDropper.Agent.ACS]
127.0.0.1  www.eurodialer.com
127.0.0.1  www.eurolive.com
127.0.0.1  statsv3.gaycash.com
127.0.0.1  ipigz.com
127.0.0.1  www.ipigz.com
127.0.0.1  16755.dialer.lincassa.com #[HJTH.Carpediem Dialer]
127.0.0.1  17067.dialer.lincassa.com
127.0.0.1  20429.dialer.lincassa.com #[Win32/Dialer.CDDial]
127.0.0.1  21294.dialer.lincassa.com
127.0.0.1  www.monliveshow.com
127.0.0.1  htmldialer.parisvoyeur.com
127.0.0.1  www.parisvoyeur.com #[Dialer.Pornosex][Trojan.Win32.Dialer.eg]
127.0.0.1  www.sfondatanale.com
127.0.0.1  dialer.sponsorhispano.com #[Win32/Dialer.CDDial]
127.0.0.1  carpediem.sv2.biz
127.0.0.1  dvdmanager-203.sv2.biz
127.0.0.1  ktu.sv2.biz
# [Coulomb Ltd Group][eTrust.Coulomb Dialer]
127.0.0.1  www.coulomb.co.uk #[Dialer.Flatfive\Girlshost\Pornpaq]
127.0.0.1  dialeraccess.com #[Dialer.Postbas]
127.0.0.1  www.dialeraccess.com
127.0.0.1  www.globalcharge.com
127.0.0.1  dload.ipbill.com #[MVPS.Criteria][Win32/TrojanDownloader.Small.ON]
127.0.0.1  mojo.ipbill.com
127.0.0.1  pornsites.ipbill.com
127.0.0.1  soldproxy1.ipbill.com
127.0.0.1  tracking.ipbill.com
127.0.0.1  mobilesexpalace.com
127.0.0.1  www.pornsexpalace.com
127.0.0.1  access.premiumbilling.com
127.0.0.1  adm.gw.premiumbilling.com
127.0.0.1  gw.premiumbilling.com
127.0.0.1  www.premiumbilling.com
127.0.0.1  www.saristar.com
127.0.0.1  www.smssexpalace.com
127.0.0.1  www.valentinesmms.com #[mojo.ipbill.com]
127.0.0.1  www.valmob.com #[mojo.ipbill.com]
# [Crontel Ltd][AIS Systems Limited]
127.0.0.1  ws.aissys.com
127.0.0.1  www.andlotsmore.com #[Trojan-Downloader.Win32.Small.qy]
127.0.0.1  www.games-factory.com #[ClickYes2Enter Dialer]
127.0.0.1  community.globaleaccess.com #[W32/Malware]
127.0.0.1  trade.globaleaccess.com
127.0.0.1  www.globaleaccess.com
127.0.0.1  membersplayground.com
127.0.0.1  www.membersplayground.com #[Dialer.PlayGames]
# [Daniel Forrester]
127.0.0.1  www.lovelycum.com #[NOD32.Win32/Dialer.HZ]
127.0.0.1  www.sesso-it.com #[Trojan.Win32.Dialer.hz]
# [Global Acces S.L.]
127.0.0.1  www.dialerplatform.com #[Trojan.Ibiza]
127.0.0.1  www.ezdialeronline.com
127.0.0.1  www.global-acces.com #[Dialer.Globalacces]
127.0.0.1  www.global-access.com
127.0.0.1  access.juicyteenporn.com #[Dialer.Juicyteen][directplugin.com]
127.0.0.1  members.juicyteenporn.com #[DIAL_ATMOS.A][Porn-Dialer.Win32.GBDialer.d]
# [Electronic Group Interactive]
127.0.0.1  093qpeuqpmz6ebfa.com #[Trojan.TrustedZone]
127.0.0.1  0texkax7c6hzuidk.com #[usa-scripts.downloadv3.com]
127.0.0.1  www.1qiq0okzb7hcb3xr.com #[scripts.dlv4.com]
127.0.0.1  www.0texkax7c6hzuidk.com
127.0.0.1  www.02kmky1xgzbmsdfx.com
127.0.0.1  api.aveno.net
127.0.0.1  em.aveno.net
127.0.0.1  pics.aveno.net
127.0.0.1  secure.aveno.net
127.0.0.1  cash-explorer.com
127.0.0.1  www.cash-explorer.com
127.0.0.1  akamai.downloadv3.com #[EGP2ECOM Class][InstantAccess]
127.0.0.1  fr4-scripts.downloadv3.com
127.0.0.1  scripts.downloadv3.com
127.0.0.1  update.downloadv3.com
127.0.0.1  usa-scripts.downloadv3.com
127.0.0.1  es6-scripts.dlv4.com #[Win32/P2E]
127.0.0.1  scripts.dlv4.com #[Backdoor.Win32.PcClient.pb]
127.0.0.1  us2-scripts.dlv4.com
127.0.0.1  www.dvd-explorer.com
127.0.0.1  www.egisupport.com
127.0.0.1  mirrors.egwn.net
127.0.0.1  pubvideo3.egwn.net
127.0.0.1  server02.us2.egwn.net
127.0.0.1  static.egwn.net
127.0.0.1  www.e-group.org
127.0.0.1  support.electronic-group.com
127.0.0.1  www.electronic-group.com #[Win32.Wintrim.U]
127.0.0.1  legal.electronic-group.com
127.0.0.1  www.email-explorer.com
127.0.0.1  promo.epass-key.com
127.0.0.1  redirect.epass-key.com
127.0.0.1  www.epass-key.com
127.0.0.1  ispdialer.com #[Parasite.ACXInstall]
127.0.0.1  www.ispdialer.com
127.0.0.1  es6-scripts.nccgateway.com
127.0.0.1  access.rapid-pass.net #[network.nocreditcard.com]
127.0.0.1  help.rapid-pass.net
127.0.0.1  media.rapid-pass.net #[SunBelt.Rapid-pass.net]
127.0.0.1  public-contentv4.rapid-pass.net
127.0.0.1  www.rapid-pass.net #[Dialer.InstantAccess][DIAL_NSTANTXS.A]
127.0.0.1  sa.secure-firewall.com #[Adware.Slagent][Parasite.MagicControl]
127.0.0.1  spyware-secure.com
127.0.0.1  www.spyware-secure.com
127.0.0.1  www.traffic-converter.com
127.0.0.1  usa-network.video-party.com #[HTMLAccess Class]
127.0.0.1  www.videoparty.com
127.0.0.1  banners.vizit.us
127.0.0.1  network.vizit.us
127.0.0.1  www.vizit.us
# [PHILLIPS BRENT][NOCREDITCARD NETWORK S.L]
127.0.0.1  www.123ticket.com
127.0.0.1  www.chargemelater.com
127.0.0.1  banners.nocreditcardgay.com
127.0.0.1  instant-access.nocreditcardgay.com
127.0.0.1  network.nocreditcardgay.com
127.0.0.1  usa-network.nocreditcardgay.com
127.0.0.1  www.nocreditcardgay.com
127.0.0.1  nocreditcard.com #[TROJ_ISBAR.A]
127.0.0.1  banners.nocreditcard.com
127.0.0.1  fr4-network.nocreditcard.com
127.0.0.1  instant-access.nocreditcard.com #[Parasite.MagicControl]
127.0.0.1  network.nocreditcard.com
127.0.0.1  usa-network.nocreditcard.com
127.0.0.1  webmaster.nocreditcard.com
127.0.0.1  nocreditcard.net #[ACXInstall][DIAL_DIALEX.A]
127.0.0.1  instant-access.nocreditcard.net
127.0.0.1  network.nocreditcard.net
127.0.0.1  www.nocreditcard.net #[McAfee.Adware-EGroup]
127.0.0.1  www.one2one.com #[One2One Viewer]
127.0.0.1  cc.sex-explorer.com
127.0.0.1  contents.sex-explorer.com
127.0.0.1  static.contents.sex-explorer.com
127.0.0.1  freecc.sex-explorer.com
127.0.0.1  instant-access.sex-explorer.com
127.0.0.1  live.sex-explorer.com #[McAfee.Adware-EGroup]
127.0.0.1  lives.sex-explorer.com
127.0.0.1  ncc.sex-explorer.com
127.0.0.1  static.sex-explorer.com
127.0.0.1  trial.sex-explorer.com
127.0.0.1  xxx.sex-explorer.com
127.0.0.1  www.sex-explorer.com
127.0.0.1  network.strip-player.com
127.0.0.1  stripplayer.com #[Parasite.StripPlayer]
127.0.0.1  network.stripplayer.com
127.0.0.1  webmaster.stripplayer.com
127.0.0.1  www.strip-player.com
127.0.0.1  fun.zipzappromos.com
127.0.0.1  promo.zipzappromos.com
127.0.0.1  www.zipzappromos.com
# [LinkAutomatici Dot Com Group]
127.0.0.1  www.areasex.biz #[Trojan.Win32.Dialer.hz]
127.0.0.1  www.archiviosex.net #[Trojan.TrustedZones]
127.0.0.1  hastalavista.it #[Trojan.Win32.Dialer.hz]
127.0.0.1  www.hastalavista.it #[Trojan.TrustedZones]
127.0.0.1  www.linkautomatici.com #[Trojan.TrustedZones]
127.0.0.1  redfunny.com #[SiteAdvisor.redfunny.com]
127.0.0.1  www.redfunny.com #[Adult Content Dialer][Trojan.TrustedZones]
127.0.0.1  skymasters.biz #[SiteAdvisor.skymasters.biz]
127.0.0.1  www.skymasters.biz #[Trojan.TrustedZones][HJTH.Adult Content Dialer]
# [LinkAutomatici via Master 69 dot Com Group]
127.0.0.1  master69.biz
127.0.0.1  www.master69.biz #[DIAL_XVIDEO.A]
127.0.0.1  mastersessantanove.biz
127.0.0.1  mastersessantanove.com
# [Live Interactive S.R.L.][Adultocheck S.L][Global Business Premium Partnership]
127.0.0.1  banners.amoestecuzinho.com
127.0.0.1  banners.animeerotico.com
127.0.0.1  banners.bebadasousadas.com
127.0.0.1  banners.chicashumedas.com
127.0.0.1  banners.colegialasdesvirgadas.com
127.0.0.1  banners.debuteamador.com
127.0.0.1  galleries.ebonyempire.com
127.0.0.1  banners.espiasadictos.com
127.0.0.1  banners.fuckingdrunks.com
127.0.0.1  galleries.fuckingdrunks.com
127.0.0.1  banners.imperioanal.com
127.0.0.1  banners.lesbianascerdas.com
127.0.0.1  www.mildescargas.com #[HJTH.SponsorAdulto Dialer]
127.0.0.1  banners.mulherescomcigarros.com
127.0.0.1  galleries.negrasporno.com
127.0.0.1  www.negrasporno.com
127.0.0.1  banners.orgiasreales.com
127.0.0.1  adult.phoneaccess.com
127.0.0.1  ad1.banners.phoneaccess.com
127.0.0.1  exit.phoneaccess.com
127.0.0.1  iframe.phoneaccess.com
127.0.0.1  ipdata.phoneaccess.com #[HJTH.Dialer.NBQ]
127.0.0.1  promos.phoneaccess.com
127.0.0.1  banners.paixaogay.com
127.0.0.1  banners.paixaoasiatica.com
127.0.0.1  banners.passeilimitado.com
127.0.0.1  banners.pollasde30cm.com
127.0.0.1  banners.prazerlesbico.com
127.0.0.1  banners.sandralatina.com
127.0.0.1  galleries.schwarzesimperium.com
127.0.0.1  banners.showdeinfieles.com
127.0.0.1  banners.showdeinfieis.com
127.0.0.1  banners.sotransexuais.com
127.0.0.1  banners.spacash.com
127.0.0.1  banners2.spacash.com
127.0.0.1  banners3.spacash.com
127.0.0.1  exit.spacash.com
127.0.0.1  freesites.spacash.com
127.0.0.1  ip.spacash.com #[HJTH.SponsorAdulto Dialer]
127.0.0.1  movies.spacash.com
127.0.0.1  notice.spacash.com
127.0.0.1  rotations.spacash.com
127.0.0.1  www.spacash.com
127.0.0.1  sponsoradulto.com
127.0.0.1  banners.sponsoradulto.com
127.0.0.1  banners2.sponsoradulto.com
127.0.0.1  ip.sponsoradulto.com #[Trojan.Win32.Dialer.fu]
127.0.0.1  www.sponsoradulto.com #[HJTH.SponsorAdulto Dialer]
127.0.0.1  ip.sponsorix.com
127.0.0.1  banners.taxindecente.com
127.0.0.1  banners.teenfunzone.com
127.0.0.1  galleries.teenfunzone.com
127.0.0.1  banners.vivilatina.com
127.0.0.1  www.webspacemania.com #[SiteAdvisor.webspacemania.com]
# [Ludos adv. ltd]
127.0.0.1  www.celebrita-nude.com
127.0.0.1  www.celebritasenzaveli.com
127.0.0.1  www.eros-porno.com
127.0.0.1  www.omniasex.com
# [Madison Administration]
127.0.0.1  7adpower.com #[ADW_ADPOWER.D]
127.0.0.1  www.7adpower.com #[HJTH.Svezia.Dialer]
127.0.0.1  advnt.com
127.0.0.1  www.advnt.com
127.0.0.1  advnt01.com #[HJTH.7AdPower Dialer][DIAL_ADPOWER.B]
127.0.0.1  ocx2.advnt01.com #[HJTH.7AdPower Dialer]
127.0.0.1  ocx3.advnt01.com
127.0.0.1  www9.advnt01.com #[Porn-Dialer.Win32.Creazione.i]
127.0.0.1  www.advnt01.com #[HJTH.7AdPower Dialer]
127.0.0.1  advnt02.com
127.0.0.1  www.advnt02.com
127.0.0.1  advnt03.com #[HJTH.7AdPower Dialer]
127.0.0.1  advnt04.com
127.0.0.1  advnt05.com
127.0.0.1  www.globalphon.com #[Dialer.7AdPower]
# [Mainpean GmbH][Adware.Mainpean]
127.0.0.1  faq.mainpean.de
127.0.0.1  voicecall.mainpean.de
127.0.0.1  www.mainpean.de #[Dailer.Megateens]
127.0.0.1  stardialer.de #[DIAL_PORNDIAL.CA]
127.0.0.1  help.stardialer.de #[Parasite.StarDialer]
127.0.0.1  install.stardialer.de #[Installations Assistent]
127.0.0.1  www.stardialer.de #[Dialer.Stardial]
# [NetVenda Group]
127.0.0.1  l00kl23.com #[HJTH.NetVenda Dialer]
127.0.0.1  netvenda.com
127.0.0.1  content.netvenda.com
127.0.0.1  content2.netvenda.com
127.0.0.1  www.netvenda.com #[HJTH.NetVenda Dialer]
127.0.0.1  playqames.com #[HJTH.NetVenda Dialer]
# [New Harmony Enterprises][Dialer.MovieFile]
127.0.0.1  www.247cams.com
127.0.0.1  mediacharger.com
127.0.0.1  devfast.mediacharger.com
127.0.0.1  download.mediacharger.com
127.0.0.1  fast.mediacharger.com #[MediaCharger\MoviePlace]
127.0.0.1  www.pml.mediacharger.com
127.0.0.1  www.movienetworks.com
127.0.0.1  members.swimsuitnetwork.com #[Panda.Adware:swimsuitnetwork]
127.0.0.1  www.swimsuitnetwork.com #[SwimSuitNetwork Direct]
# [Niker Oldman]
127.0.0.1  newxhard.com
127.0.0.1  xthehun.com #[TR/Spy.Stac.C][Win32/Wussoe.B]
127.0.0.1  casino.xthehun.com
127.0.0.1  gambling.xthehun.com
127.0.0.1  online.xthehun.com
127.0.0.1  www.xthehun.com #[IFrame.Exploit]
# [Softlab Group]
127.0.0.1  www.adslconnection.name #[Trojan.TrustedZone]
127.0.0.1  www.xxx-content.name #[Trojan.TrustedZone]
# [Tanzania Import]
127.0.0.1  www.analcord.com #[Downloader.Goobiz]
127.0.0.1  www.preferiti-windows.com #[Trojan-Clicker.Win32.Agent.ip]
127.0.0.1  www.therealbigg.com
# [Viper BV]
127.0.0.1  www.erodynamics.nl
127.0.0.1  klikbonus.com
127.0.0.1  www.klikbonus.com
127.0.0.1  x0.nl #[dialXS]
127.0.0.1  www.x0.nl #[Win32/Dialer.DialSX]
# [World Telecom]
127.0.0.1  download.energy-factor.com #[HJTH.Trojan.Downloader.Small]
127.0.0.1  www.energyplugin.com #[eTrust.EnergyPlugin][Trojan.Win32.Energy.A]
# [Various Adult Sites]
127.0.0.1  0nlyzoo.com #[Malicious.Links]
127.0.0.1  www.0nlyzoo.com
127.0.0.1  0traff.com
127.0.0.1  1amanda.info #[Spamdexing]
127.0.0.1  www.100dreamgirls.com #[Google.Warning]
127.0.0.1  100js.org #[Spamdexing]
127.0.0.1  1000pornvids.com #[IFrame.Exploit]
127.0.0.1  1speed.info #[Malicious.Links]
127.0.0.1  123-music-video.info #[Malicious Links][server down?]
127.0.0.1  12345dns.net #[Videoscash]
127.0.0.1  103bees.com
127.0.0.1  2k-sex.com #[Porn-Dialer.Win32.Madial.a]
127.0.0.1  2younger.com
127.0.0.1  www.2younger.com #[IFrame.Exploit]
127.0.0.1  3xpicsmovies.com #[Malicious.Links]
127.0.0.1  3younggirls.com #[Malicious Links]
127.0.0.1  404e.com
127.0.0.1  4divx.com #[IFrame.Exploit]
127.0.0.1  ads.6agenten.dk
127.0.0.1  www.777-sex.com #[Malicious Links]
127.0.0.1  777-teens.com #[IFrame.Exploit]
127.0.0.1  www.777-teens.com
127.0.0.1  www.7days.ws #[Troj/IEStart-F]
# [A]
127.0.0.1  www.absolutefreesmut.com #[Win32/TrojanDownloader.IstBar.S]
127.0.0.1  adchimp.com
127.0.0.1  ad.abum.com
127.0.0.1  ads.adgenta.com
127.0.0.1  page1.adroup.com
127.0.0.1  adinoyman.info #[Malicious Links]
127.0.0.1  www.adloader.com
127.0.0.1  www.ad-pay.de
127.0.0.1  adrianakarembeu.org #[Malicious Links]
127.0.0.1  www.ads180.com
127.0.0.1  www.adsforadults.com
127.0.0.1  adserve.adtoll.com
127.0.0.1  www.adult2006.com
127.0.0.1  www.adultadbroker.com
127.0.0.1  www.adultads.biz
127.0.0.1  www.adultbannerexchange.nl
127.0.0.1  www.adultscandy.com #[SiteAdvisor.adultscandy.com]
127.0.0.1  counter.adultcheck.com
127.0.0.1  scripts.adultcheck.com
127.0.0.1  adult-banners.co.uk
127.0.0.1  www.adultbanners.co.uk
127.0.0.1  www.adult-banner-ads.com
127.0.0.1  www.adultbannerswap.co.uk
127.0.0.1  www.adultdream.org #[Spamdexing]
127.0.0.1  www.adultdvdhits.com
127.0.0.1  adultfreevideos.net
127.0.0.1  www.adultfreevideos.net #[Malicious.Links.Videoscash]
127.0.0.1  www.adultkeeper.com #[SiteAdvisor.adultkeeper.com]
127.0.0.1  adultlisting.info
127.0.0.1  www.adult-models.org #[JS/Exploit.MS05-013]
127.0.0.1  adultonlineservices.info
127.0.0.1  www.adultpla.net #[Malicious.Links]
127.0.0.1  www.adultonlineservices.info #[Malicious.Links.Videoscash]
127.0.0.1  adultsexkey.com #[Malicious.Links.Videoscash]
127.0.0.1  www.adultpagerank.com
127.0.0.1  adultvidsportal.info #[Malicious.Links]
127.0.0.1  www.adultvidsportal.info
127.0.0.1  adultwebmastersonline.com #[MHTMLRedir.Exploit][traffnew.biz]
127.0.0.1  www.adultwebmastersonline.com #[SiteAdvisor.adultwebmastersonline.com]
127.0.0.1  adult-xxx-porn.info #[Malicious.Links]
127.0.0.1  www.adult-xxx-porn.info
127.0.0.1  www.adv-italia.com
127.0.0.1  banners.adventory.com
127.0.0.1  advert.hu
127.0.0.1  www.advertising-department.com
127.0.0.1  dn.adzerver.com
127.0.0.1  temp.adzerver.com
127.0.0.1  banners.affiliatefuture.com
127.0.0.1  ads.afixi.com
127.0.0.1  err.agava.ru
127.0.0.1  alinaalbum.com #[Malicious.Links]
127.0.0.1  www.alinaalbum.com
127.0.0.1  all1count.net #[JS/Exploit.BO.NAA]
127.0.0.1  all3xxx.com #[Malicious.Links]
127.0.0.1  all-here.org #[Spamdexing]
127.0.0.1  www.all-here.org
127.0.0.1  femdom.allkindsofbdsm.com
127.0.0.1  films.allkindsofbdsm.com
127.0.0.1  killing.allkindsofbdsm.com #[Google Warning]
127.0.0.1  spanking.allkindsofbdsm.com
127.0.0.1  alloha.info #[Malicious Links]
127.0.0.1  allsexvids.net
127.0.0.1  www.allsexvids.net #[Malicious.Links]
127.0.0.1  alltraff.info #[Spamdexing]
127.0.0.1  all-xxx-vogue.com
127.0.0.1  alania-thumbs.com
127.0.0.1  ads.amateurmatch.com
127.0.0.1  ads2.amateurmatch.com
127.0.0.1  amateur-porn-links.com #[Malicious.Links]
127.0.0.1  amazing-gals.com 
127.0.0.1  www.amazing-gals.com #[Malicious.Links.Videoscash]
127.0.0.1  amhen.com.ru #[Umax]
127.0.0.1  banners.amsterdamcash.com
127.0.0.1  analpornvids.org #[Malicious.Links]
127.0.0.1  a-n-d-the.com #[Spamdexing]
127.0.0.1  angelsvids.com
127.0.0.1  www.angelsvids.com #[Malicious Links]
127.0.0.1  anytraff.com
127.0.0.1  track.apexstats.com
127.0.0.1  armedteens.com #[Malicious.Links]
127.0.0.1  www.armedteens.com
127.0.0.1  aretheymales.com #[Malicious.Links]
127.0.0.1  web16.saturn101.art-customer.net #[JS/Exploit.MS05-013]
127.0.0.1  ads.asexstories.com
127.0.0.1  ads.asredas.com
127.0.0.1  www.attractivesex.com #[Malicious.Links]
127.0.0.1  adson.awempire.com
127.0.0.1  counter.awempire.com
127.0.0.1  iframes.awempire.com
127.0.0.1  promo.awempire.com
127.0.0.1  stats.awms-network.com
# [B]
127.0.0.1  livechat.babes-wallpaper.com
127.0.0.1  www.babes-wallpaper.com #[Malicious Links]
127.0.0.1  banners.babylon-x.com
127.0.0.1  banit.info #[Spamdexing]
127.0.0.1  www.banner.cz
127.0.0.1  adv.bannercity.ru
127.0.0.1  link.bannersystem.cz
127.0.0.1  barmalei.info #[Spamdexing]
127.0.0.1  baxet.com #[Spamdexing]
127.0.0.1  www.bdsm2k.com #[IFrame.Exploit]
127.0.0.1  www.bdsmathome.info #[Malicious.Links]
127.0.0.1  www.bdsmxxxmovies.com #[Malicious.Links]
127.0.0.1  ad.beleveyou.com
127.0.0.1  beregs.info #[Videoscash]
127.0.0.1  www.best-adult-pics.org #[Spamdexing]
127.0.0.1  bestadultsearch.net
127.0.0.1  www.bestadultsites.biz
127.0.0.1  bestestporn.com #[Videoscash]
127.0.0.1  bestfamilysex.info
127.0.0.1  www.bestfamilysex.info #[IFrame.Exploit]
127.0.0.1  bestfreemature.com #[IFrame.Exploit]
127.0.0.1  bestfriendvids.com
127.0.0.1  www.bestfriendvids.com #[Javascript.Exploit]
127.0.0.1  bestga.biz #[thetraff.com]
127.0.0.1  www.bestgirls.name #[Malicious Links]
127.0.0.1  bestjizz.com #[Malicious.Links]
127.0.0.1  www.bestjizz.com
127.0.0.1  bestmatures.net #[Videoscash]
127.0.0.1  www.bestmatures.net
127.0.0.1  a.bestmanage.org
127.0.0.1  b.bestmanage.org
127.0.0.1  c.bestmanage.org
127.0.0.1  d.bestmanage.org #[TR/Dldr.Agent.11776]
127.0.0.1  s2.bestmanage.org
127.0.0.1  setup.bestmanage.org #[JS/TrojanDownloader.Psyme.CG]
127.0.0.1  a.bestmanage1.org
127.0.0.1  zero.bestmanage2.org
127.0.0.1  zero.bestmanage3.org #[Google.Warning]
127.0.0.1  www.bestmoms.net
127.0.0.1  bestmygalleries.com #[Malicious.Links]
127.0.0.1  bestnetporn.com
127.0.0.1  best-results-now.info #[IFrame.Exploit]
127.0.0.1  bestsearchlink.com #[Spamdexing]
127.0.0.1  bestteenspics.com #[IFrame.Exploit]
127.0.0.1  www.best-top.de
127.0.0.1  www.bestscripting.com
127.0.0.1  www.bestseofinder.info
127.0.0.1  best-sites-only.info
127.0.0.1  bestteenz.info
127.0.0.1  betterclips.com
127.0.0.1  www.betterclips.com
127.0.0.1  www.bigmpegx.com #[Malicious.Links]
127.0.0.1  billpics.com #[Malicious Links]
127.0.0.1  blacksnake.com
127.0.0.1  www.blacksnake.com #[IRC.Trojan.Fgt]
127.0.0.1  bleso.com #[Spamdexing][winantispyware.com]
127.0.0.1  banners.blingbucks.com
127.0.0.1  bonass.net #[go.winantispyware.com]
127.0.0.1  www.bonass.net
127.0.0.1  bondagevideos.us #[IFrame.Exploit]
127.0.0.1  www.bondagevideos.us
127.0.0.1  boomsearch.info #[Videoscash][Google Warning]
127.0.0.1  bootylist.com #[HTML/TrojanDownloader.XXXToolbar]
127.0.0.1  boysfood.com #[Malicious.Content.Zango]
127.0.0.1  breakteen.com
127.0.0.1  www.breakteen.com
127.0.0.1  www.bringmemovie.com #[IFrame.Exploit]
127.0.0.1  brothervids.com #[IFrame.Exploit]
127.0.0.1  www.brothervids.com
127.0.0.1  www.browseadult.com
127.0.0.1  www.brsexo.org #[IFrame.Exploit]
# [C]
127.0.0.1  ads.host.camz.com
127.0.0.1  logger.cash-media.de
127.0.0.1  stats.cashring.com
127.0.0.1  adv.casinopays.com
127.0.0.1  crbanner.casinopays.com
127.0.0.1  cawajanga.biz #[Javascript.Exploit]
127.0.0.1  banner.cdpoker.com
127.0.0.1  celebflix.us
127.0.0.1  www.celebflix.us #[Videoscash]
127.0.0.1  celebpix.org
127.0.0.1  r.celebz.ru
127.0.0.1  centralcoastihop.net #[Spamdexing]
127.0.0.1  ceporno.com #[Malicious.Links]
127.0.0.1  adv.cgiworld.net
127.0.0.1  count.cgiworld.net
127.0.0.1  err.chicappa.jp
127.0.0.1  chicks4jerk.com #[Malicious.Links]
127.0.0.1  chicksbox.com
127.0.0.1  www.chicksbox.com #[Javascript.Exploit]
127.0.0.1  best.clean-porno.com #[Spamdexing]
127.0.0.1  hit.clickaider.com
127.0.0.1  hit.dev.clickaider.com
127.0.0.1  banners.clickthrucash.com
127.0.0.1  www.clickthruserver.com
127.0.0.1  www.clipslist.com #[Google.Warning]
127.0.0.1  clips1000.com #[IFrame.Exploit]
127.0.0.1  www.clips1000.com
127.0.0.1  banners.clips4sale.com
127.0.0.1  clipslist.com #[Google.Warning]
127.0.0.1  clubonly18.com #[MHTMLRedir.Exploit][server down?]
127.0.0.1  www.clubonly18.com
127.0.0.1  www.cocogals.com #[Spamdexing][Trojan.Codec]
127.0.0.1  img.comparefacil.com
127.0.0.1  www.comparefacil.com
127.0.0.1  compays.com
127.0.0.1  www.contractorstar.com #[Spamdexing]
127.0.0.1  cool4free.org #[Spamdexing][Malicious.Links.drivecleaner.com]
127.0.0.1  search.cool4free.org
127.0.0.1  coolfuckgirl.com #[Malicious Links]
127.0.0.1  www.coolfuckgirl.com
127.0.0.1  counter.cnw.cz
127.0.0.1  www.count24.de
127.0.0.1  counter4all.dk
127.0.0.1  links.crackportal.com #[SiteAdvisor.crackportal.com]
127.0.0.1  www.crackportal.com #[Trojan.Win32.Favadd.d]
127.0.0.1  crackspider.net #[Trojan.Favadd]
127.0.0.1  www.crackspider.net #[Trojan.Win32.StartPage.fg]
127.0.0.1  crazyegg.com
127.0.0.1  www.credonic.com
127.0.0.1  www.cross-nation-couples.org #[Malicious.Links]
127.0.0.1  ctynn.com
127.0.0.1  www.ctynn.com #[Videoscash]
127.0.0.1  cumoncelinedion.info #[Malicious Links][MIRT]
127.0.0.1  www.cunnilinguo.com
127.0.0.1  cunnyhoney.com
127.0.0.1  www.cunnyhoney.com
127.0.0.1  www.cuterussianboys.com #[Google Warning]
127.0.0.1  cutevoyeur.com #[Videoscash]
127.0.0.1  www.cybilling.com
127.0.0.1  cyberfind10.info #[Spamdexing]
127.0.0.1  banner.czech-sex.cz
# [D]
127.0.0.1  dailyxxvids.com
127.0.0.1  www.dailyxxvids.com
127.0.0.1  www.daisygalz.com #[Javescript.Exploit]
127.0.0.1  damnvids.com
127.0.0.1  www.damnvids.com #[Malicious Links]
127.0.0.1  dan-online.biz #[Spamdexing]
127.0.0.1  www.danworld.net #[content.yieldmanager.com]
127.0.0.1  xxx.dataseeq.com
127.0.0.1  z.dataseeq.com #[Spamdexing]
127.0.0.1  www.databaseporno.com #[Malicious Links][server down?]
127.0.0.1  top.dating.lt #[counter.top.dating.lt]
127.0.0.1  www.dbobs.com #[Spamdexing]
127.0.0.1  demo-sex.com #[Malicious Links]
127.0.0.1  densmail.com #[Javascript.Exploit]
127.0.0.1  denmovies.com #[IFrame.Exploit]
127.0.0.1  ads.desktopscans.com
127.0.0.1  banners.direction-x.com
127.0.0.1  www.directoryadult.com
127.0.0.1  server2.discountclick.com
127.0.0.1  www.divx.it
127.0.0.1  dobondage.com #[IFrame.Exploit]
127.0.0.1  www.dobondage.com
127.0.0.1  www.do-friend.com #[IFrame.Exploit]
127.0.0.1  doorshost.com
127.0.0.1  downloadz.us #[Spamdexing]
127.0.0.1  click.dpbill.com
127.0.0.1  www.dplog.com #[MHTMLRedir.Exploit]
127.0.0.1  www.dragon-balls.com
127.0.0.1  www.dropdeadugly.com #[Malicious.Links.Zango]
127.0.0.1  drunkporn.us
127.0.0.1  dzheker.com
# [E]
127.0.0.1  ebonysexzone.com #[IFrame.Exploit]
127.0.0.1  ehho.com
127.0.0.1  elmansion.com
127.0.0.1  www.elmansion.com #[Malicious Links]
127.0.0.1  www.enormousdating.com
127.0.0.1  eosws.org #[Malicious Links]
127.0.0.1  epicteen.com
127.0.0.1  www.epicteen.com #[IFrame.Exploit]
127.0.0.1  clicks.equantum.com
127.0.0.1  doollli.erotic-place.org #[Google Warning]
127.0.0.1  gayporn.erotic-place.org
127.0.0.1  pustoaice.erotic-place.org
127.0.0.1  ban.erovideo.ru
127.0.0.1  esibizioniste.org
127.0.0.1  www.esibizioniste.org #[IFrame.Exploit]
127.0.0.1  e-tst.com #[Videoscash]
127.0.0.1  www.e-tst.com
127.0.0.1  www.etushow.com
127.0.0.1  evil-x.org #[Javascript.Exploit][server down?]
127.0.0.1  exclusive-porn.info #[Malicious.Links]
127.0.0.1  www.exitmoney.com
127.0.0.1  www.eroticsgirl.com #[Malicious.Content]
127.0.0.1  extra-teens.net #[Malicious Links]
127.0.0.1  www.extra-teens.net
127.0.0.1  extramoms.com #[IFrame.Exploit]
127.0.0.1  extrasexmovie.com #[Javascript.Exploit]
127.0.0.1  www.extrasexmovie.com #[Malicious Links]
127.0.0.1  extremeforlife.net #[Spamdexing]
127.0.0.1  extreme-juggs.com #[Malicious.Links.Codec]
127.0.0.1  www.extreme-juggs.com
127.0.0.1  extreme-mpeg.com #[Malicious.Links]
127.0.0.1  extremevideoz.net #[Malicious.Links]
127.0.0.1  extreme-tranny.extremevideoz.net #[IFrame.Exploit]
# [F]
127.0.0.1  www.faceoffgirls.com #[IFrame.Exploit]
127.0.0.1  feralsex.com #[Google.Warning]
127.0.0.1  www.filmpjes.us #[DIAL_DIALXS.A]
127.0.0.1  www.film-x-gratos.com #[Malicious Links]
127.0.0.1  findsnd.com #[Spamdexing]
127.0.0.1  findsns.com #[Spamdexing]
127.0.0.1  finesexpix.com #[Malicious.Links]
127.0.0.1  fist-sex.info
127.0.0.1  www.flash-stat.com
127.0.0.1  promos.fling.com
127.0.0.1  www.forestincest.com #[IFrame.Exploit]
127.0.0.1  for-movies.net #[Spamdexing]
127.0.0.1  foteens.com #[IFrame.Exploit]
127.0.0.1  freakyyoung.com #[Malicious.Links][server down?]
127.0.0.1  free3xmovies.com #[Trojan.Codec]
127.0.0.1  freedataweb.com
127.0.0.1  www.free-hardcoresex.org
127.0.0.1  xyz.freeweblogger.com
127.0.0.1  freeporn-4you.info #[IFrame.Exploit]
127.0.0.1  ltds.freeporn4you.info
127.0.0.1  www.freeporn-mpegs.com
127.0.0.1  freeporn-search.com
127.0.0.1  free-porn-movies.info #[Win32/TrojanDownloader.WarSpy][server down?]
127.0.0.1  tds.free-porn-movies.info
127.0.0.1  www.free-porn-movies.info
127.0.0.1  www.free-rape-pics.us
127.0.0.1  www.freepicsandmovies.com #[Win32/Dialer.Asian.RAW]
127.0.0.1  www.freerealitymovs.com #[Malicious.Links]
127.0.0.1  freeskivideo.info #[Malicious.Links]
127.0.0.1  www.free-toplisten.at
127.0.0.1  www.freeteensets.com #[Spamdexing]
127.0.0.1  freevideo.in #[Videoscash]
127.0.0.1  freex3movies.com
127.0.0.1  www.freex3movies.com
127.0.0.1  freeyoungcelebs.org #[Spamdexing]
127.0.0.1  www.freshpornlinks.com
127.0.0.1  c.fsx.com
127.0.0.1  adserver.fuckaroo.org
127.0.0.1  www.fuckingmotherfucker.com #[Malicious.Links.Zango]
127.0.0.1  fuckphent.com
127.0.0.1  www.fuckteenpussy.net #[Malicious Links]
127.0.0.1  ads.fuckyoupayme.com
127.0.0.1  funadult.net #[Videoscash]
127.0.0.1  www.funadult.net
127.0.0.1  funlivesex.info #[Spamdexing]
# [G]
127.0.0.1  xxx.galleryporn.net #[MHTMLRedir.Exploit]
127.0.0.1  www.gallery-of-porn.net #[Trojan.Codec]
127.0.0.1  gaietymaster.com #[Videoscash]
127.0.0.1  www.gaietymaster.com
127.0.0.1  adserver.gallerytrafficservice.com
127.0.0.1  gaylovetwinks.com #[Malicious Links]
127.0.0.1  www.gaylovetwinks.com
127.0.0.1  gaytrafficbroker.com
127.0.0.1  gaytraffic.biz
127.0.0.1  gameteenvids.com #[IFrame.Exploit]
127.0.0.1  www.gameteenvids.com
127.0.0.1  www.gbcash.com
127.0.0.1  gbscript.com
127.0.0.1  gem-inc.com
127.0.0.1  getdailyimages.com #[Trojan.Codec]
127.0.0.1  www.getdailyimages.com
127.0.0.1  getpornmovie.com
127.0.0.1  www.getpornmovie.com #[Javascript.Exploit]
127.0.0.1  get-vids.com #[Videoscash]
127.0.0.1  www.get-vids.com
127.0.0.1  gpads.geniproj.com
127.0.0.1  gilorosearch.com #[Malicious.Links]
127.0.0.1  girlsmpg.com #[Malicious.Links]
127.0.0.1  girlspornonline.info #[Malicious Links][Google Warning]
127.0.0.1  arsconsole.global-intermedia.com
127.0.0.1  feeds.global-intermedia.com
127.0.0.1  clicks.globaltrafficservice.com
127.0.0.1  feeds.globaltrafficservice.com #[Spamdexing]
127.0.0.1  go4433.net #[Videoscash]
127.0.0.1  gobigtits.com #[IFrame.Exploit]
127.0.0.1  www.gobigtits.com
127.0.0.1  godefloration.net #[Videoscash]
127.0.0.1  ads.gofuckyourself.com
127.0.0.1  www.gonorar.com #[Spamdexing]
127.0.0.1  gotraf.com
127.0.0.1  grandsupertds.info #[Spamdexing]
127.0.0.1  www.grannycenter.com #[IFrame.Exploit]
127.0.0.1  error404.gratishost.com
127.0.0.1  greatteenmovies.com #[IFrame.Exploit]
127.0.0.1  greatfreevideo.com #[Trojan.Codec]
127.0.0.1  www.greatfreevideo.com
127.0.0.1  free.great-porn.net
127.0.0.1  r.great-porn.net #[Spamdexing]
127.0.0.1  banner.greatpokerclub.org #[Adware.Casino]
127.0.0.1  gusarov.net
127.0.0.1  www.gusarov.net #[Google.Warning]
# [H]
127.0.0.1  hanklist.com
127.0.0.1  www.hanklist.com
127.0.0.1  www.hardcoreamateurmoviess.com
127.0.0.1  hardfacktor.org #[Malicious Links]
127.0.0.1  www.hardfootballbabes.com #[REG_EPLUGIN.AC][Trojan.TrustedZone]
127.0.0.1  www.hardmovies.net
127.0.0.1  hardsaloon.com #[IFrame.Exploit]
127.0.0.1  www.hbcnet.com #[Spamdexing]
127.0.0.1  www.healthsourceuk.com #[Videoscash]
127.0.0.1  www.heartbabes.com #[Javascript.Exploit]
127.0.0.1  adserver.hispavista.com
127.0.0.1  www.homesexsearch.com #[Trojan.Codec]
127.0.0.1  homevidz.net #[IFrame.Exploit]
127.0.0.1  homo6.com #[Malicious.Links]
127.0.0.1  adweb1.hornymatches.com
127.0.0.1  adweb2.hornymatches.com
127.0.0.1  hornytraffic.com
127.0.0.1  www.hornytraffic.com
127.0.0.1  hornys-place.com
127.0.0.1  www.hornys-place.com #[Google Warning]
127.0.0.1  hot50babes.com #[JS/TrojanDownloader.Psyme.CZ.Gen]
127.0.0.1  www.hotelmgp.com #[Malicious Links]
127.0.0.1  hot-images.net
127.0.0.1  www.hot-images.net #[Videoscash]
127.0.0.1  hot-incest.com #[MHTMLRedir.Exploit]
127.0.0.1  www.hot-incest.com
127.0.0.1  hardpornvids.org
127.0.0.1  www.hardpornvids.org #[Malicious Links]
127.0.0.1  www.hotsexywallpapers.com #[Videoscash]
127.0.0.1  ad3.hornymatches.com
127.0.0.1  gbanners.hornymatches.com
127.0.0.1  hqpornweb.com
127.0.0.1  www.hqpornweb.com #[Videoscash]
127.0.0.1  a.hqtms.com
127.0.0.1  www.hqtms.com #[Spamdexing]
127.0.0.1  403.hqhost.net
127.0.0.1  404.hqhost.net
127.0.0.1  hqpornportal.com #[Spamdexing]
127.0.0.1  hqualitysex.com
127.0.0.1  www.hqualitysex.com #[Google.Warning]
127.0.0.1  www.hugetraffic.com
# [I]
127.0.0.1  ads.iawsnetwork.com
127.0.0.1  oreo.iawsnetwork.com
127.0.0.1  inbabes.com #[IFrame.Exploit]
127.0.0.1  ifree-search.org #[Malicious.Links]
127.0.0.1  incesta.com
127.0.0.1  www.incesta.com #[IFrame.Exploit]
127.0.0.1  www.incestcatalog.com #[IFrame.Exploit]
127.0.0.1  incestclips.net
127.0.0.1  www.incestclips.net #[Javascript.Exploit][server down?]
127.0.0.1  www.incestsexparty.com #[Malicious.Links]
127.0.0.1  incesttop.com #[IFrame.Exploit]
127.0.0.1  incest-vids.com
127.0.0.1  www.incest-vids.com #[Trojan.Codec][server down?]
127.0.0.1  exitstitial.infospacehosting.net #[InfoSpace]
127.0.0.1  incest-pics--incest.com #[under-xxx.com]
127.0.0.1  innocentflowers.com #[Malicious Links]
127.0.0.1  server2.internetdump.com
127.0.0.1  intraff.com
127.0.0.1  ciscom1.iquebec.com #[Spamdexing]
127.0.0.1  yxcv.is-a-geek.net #[smutserver.com][HJTH.Adult Content Dialer]
127.0.0.1  isellmybody.com #[Trojan.Codec]
127.0.0.1  www.isellmybody.com
127.0.0.1  www.island-women.com #[Malicious Links]
127.0.0.1  isralink.net
127.0.0.1  redirect.it-search.biz #[Malicious Links]
127.0.0.1  italiaxxxtop.com
127.0.0.1  iwantyou.name #[Malicious Links]
127.0.0.1  www.iwantyou.name
# [J]
127.0.0.1  jakpot.org #[Trojan.Codec]
127.0.0.1  www.jakpot.org
127.0.0.1  jalapenovids.com #[Malicious.Links]
127.0.0.1  janit.info #[Spamdexing]
127.0.0.1  counter.jasmin.hu
127.0.0.1  jasminemovies.com #[Malicious Links]
127.0.0.1  www.jasminemovies.com
127.0.0.1  m.javaforge.info
127.0.0.1  mj.javaforge.info #[Spamdexing]
127.0.0.1  jennympegs.com #[Malicious.Links]
127.0.0.1  jercys.com #[Spamdexing]
127.0.0.1  jizzmyhole.com #[Malicious.Links]
127.0.0.1  www.jizzmyhole.com
127.0.0.1  jlucky.com
127.0.0.1  www.joegalz.com #[Javascript.Exploit]
127.0.0.1  www.jointraffic.com
127.0.0.1  ads.jolinko.com
127.0.0.1  errors.jp18.com
127.0.0.1  j-rx.com
127.0.0.1  jsmovies.com
127.0.0.1  www.jsmovies.com #[Malicious.Links]
127.0.0.1  www.juggvideos.com #[Malicious Links]
127.0.0.1  www.juiceadv.com
127.0.0.1  www.juicyads.com
127.0.0.1  adserver.juicybucks.com
127.0.0.1  barbieshemale.just-a-porn.com #[IFrame.Exploit]
127.0.0.1  justhotnude.com
127.0.0.1  www.justhotnude.com #[Javascript.Exploit]
127.0.0.1  just-traffic.com
# [K]
127.0.0.1  ads.kaktuz.net
127.0.0.1  katiereesphotos.org #[Trojan.Codec]
127.0.0.1  www.katiereesphotos.org
127.0.0.1  keygen.us #[Troj/Favadd-D]
127.0.0.1  www.keygen.us
127.0.0.1  www.kidzilla.info #[JS/Exploit.MS05-013]
127.0.0.1  www.kingsizevideos.com #[IFrame.Exploit]
127.0.0.1  www.klikiq.com
# [L]
127.0.0.1  banners.largecash.com
127.0.0.1  www.lasthomevideo.com #[Malicious.Links]
127.0.0.1  laurampegs.com #[Malicious.Links]
127.0.0.1  click.lc-pay.com
127.0.0.1  www.lemonmov.com #[Malicious.Links]
127.0.0.1  lesbiansmovies.net #[Malicious.Links]
127.0.0.1  ads.lesbianpersonals.com
127.0.0.1  lesbian-sex.name #[Spamdexing]
127.0.0.1  www.lesbian-sex.name
127.0.0.1  counter.lgg.ru
127.0.0.1  limewax.org #[Videoscash]
127.0.0.1  links-and-traffic.com
127.0.0.1  little-amateurs.com
127.0.0.1  www.little-amateurs.com #[Videoscash]
127.0.0.1  hostit.liveadulthost.com #[Javascript.Exploit]
127.0.0.1  liveusasex.com #[Malicious.Links]
127.0.0.1  www.livewebstats.dk
127.0.0.1  www.livewebstats.net
127.0.0.1  www.logging.to
127.0.0.1  lolafree.com #[Malicious Links]
127.0.0.1  loosing-virginity.com #[Malicious Links]
127.0.0.1  lovelychix.net
127.0.0.1  www2.lovely-search.com #[Spamdexing]
127.0.0.1  www.lovelyteenvids.com #[Javascript.Exploit]
127.0.0.1  partner.loveplanet.ru
127.0.0.1  lovepic.net #[HTML/TrojanDownloader.XXXToolbar]
127.0.0.1  www.lovepic.net
127.0.0.1  www.love-world.de #[Troj/Tps]
127.0.0.1  www.lovetraffic.com
127.0.0.1  ltds.biz #[Videoscash]
127.0.0.1  ltraffic.biz #[IFrame.Exploit]
127.0.0.1  lustgal.com #[Malicious Links]
127.0.0.1  lusttop.com #[Malicious Links]
# [M]
127.0.0.1  rewards.macandbumble.com
127.0.0.1  www.madsexxx.com #[Trojan.Codec][server down?]
127.0.0.1  www.mainstreet3.com #[Spamdexing]
127.0.0.1  nub9r.maisonx.com #[BKDR_WOMANIZ.H]
127.0.0.1  www.male-celeb-videos.com #[Zango]
127.0.0.1  maleslist.com #[Videoscash]
127.0.0.1  www.maleslist.com
127.0.0.1  adult.master-tv.net
127.0.0.1  mass-traffic.com
127.0.0.1  www.maturehit.com
127.0.0.1  mature-*****.us
127.0.0.1  mature-sex-movies.com
127.0.0.1  www.mature-sex-movies.com
127.0.0.1  mauricehurstnah.com #[Google.Warning]
127.0.0.1  j.maxmind.com
127.0.0.1  click.maxxandmore.com
127.0.0.1  link.maxxandmore.com #[Spamdexing]
127.0.0.1  resources.maxcash.com
127.0.0.1  stats.maximumcash.com #[SunBelt.MaximumCash.com]
127.0.0.1  www.maximumcash.com #[Tenebril.Tracking.Cookie]
127.0.0.1  www.mdexitconsole.com
127.0.0.1  audit.median.hu
127.0.0.1  www.megacounter.de
127.0.0.1  ads.memberarea.cc
127.0.0.1  mentolix.info #[Malicious Links]
127.0.0.1  smartad.mercadolivre.com.br
127.0.0.1  ads.miarroba.com
127.0.0.1  microsoft-com.us #[IFrame.Exploit]
127.0.0.1  milky-teens.com
127.0.0.1  www.milky-teens.com #[IFrame.Exploit]
127.0.0.1  minigirls.biz #[IFrame.Exploit]
127.0.0.1  www.minigirls.biz
127.0.0.1  mixteenies.com
127.0.0.1  www.mixteenies.com #[Malicious.Links]
127.0.0.1  mnepoxuy.info #[Spamdexing]
127.0.0.1  www.momsbusters.com
127.0.0.1  momsporno.com #[Google.Warning]
127.0.0.1  moneyboobs.com #[IFrame.Exploit]
127.0.0.1  more-than-sex.com #[Malicious Links]
127.0.0.1  motosn.com #[Videoscash]
127.0.0.1  ads.movieflix.com
127.0.0.1  www.movieflowers.com #[Malicious Links]
127.0.0.1  movieslib.com
127.0.0.1  www.movieslib.com #[IFrame.Exploit]
127.0.0.1  moviesocean.com #[Malicious Links]
127.0.0.1  movingteens.com
127.0.0.1  movies4you.info #[Malicious.Links]
127.0.0.1  www.movingteens.com #[IFrame.Exploit]
127.0.0.1  movonteens.com #[Google Warning]
127.0.0.1  www.movonteens.com #[IFrame.Exploit]
127.0.0.1  mpgfuns.com
127.0.0.1  www.mpgfuns.com #[Malicious.Links]
127.0.0.1  seoprom.msk.ru
127.0.0.1  muschi-tgp.com #[IFrame.Exploit]
127.0.0.1  www.musicom-auvisa.com #[Spamdexing]
127.0.0.1  myadultgate.com #[Google Warning]
127.0.0.1  www.myadultgate.com
127.0.0.1  myadultguide.net #[Google Warning]
127.0.0.1  adult.myfreehotmovie.com #[Malicious.Content.Zango]
127.0.0.1  myfriendcamlive.com #[Trojan.Codec]
127.0.0.1  myxgirls.com #[IFrame.Exploit]
127.0.0.1  www.mypgn.com #[HTML.Exploit]
127.0.0.1  myqpu.com #[Spamdexing]
127.0.0.1  myoldwife.com #[IFrame.Exploit]
127.0.0.1  www.mysexfolder.com
127.0.0.1  www.myteenscollection.com #[Malicious Links][server down?]
127.0.0.1  mysterybdsm.com #[Videoscash]
127.0.0.1  www.mysterybdsm.com
127.0.0.1  www.myxratedlinks.com
# [N]
127.0.0.1  adserver2.n9nedegrees.com
127.0.0.1  banner.nastycash.com
127.0.0.1  clicks.nastydollars.com
127.0.0.1  grab.nastydollars.com
127.0.0.1  graphics.nastydollars.com
127.0.0.1  www.naughtysaints.com #[Malicious.Content.Zango]
127.0.0.1  nemo-movies.com #[Malicious Links]
127.0.0.1  net-pic.com #[Spamdexing][Trojan.Codec]
127.0.0.1  newmediadriver.com
127.0.0.1  newpornonline.net #[Malicious.Links]
127.0.0.1  newsvr.info #[Malicious.Links]
127.0.0.1  new-team.biz #[Spamdexing]
127.0.0.1  www.new-team.biz
127.0.0.1  banners.nichepromotion.com
127.0.0.1  www.nightherb.com
127.0.0.1  nisya-girls.info #[IFrame.Exploit][server down?]
127.0.0.1  counter.nope.dk
127.0.0.1  nudegalleries.org #[Malicious.Links.Codec]
127.0.0.1  www.nudegalleries.org
127.0.0.1  www.nudegayvideos.com #[Malicious.Links.Zango]
127.0.0.1  nudeteens.in #[JS/TrojanDownloader.Psyme.CZ.Gen]
127.0.0.1  www.nudeteens.in
127.0.0.1  www.nzads.net.nz
# [O]
127.0.0.1  oemfonts.hk #[Javascript.Exploit]
127.0.0.1  offgirls.com #[IFrame.Exploit]
127.0.0.1  www.offgirls.com
127.0.0.1  ohporn.com #[Videoscash]
127.0.0.1  www.ohporn.com
127.0.0.1  www.oh-porn.net #[Malicious.Links]
127.0.0.1  counter.ok.ee
127.0.0.1  olderpassion.com #[IFrame.Exploit]
127.0.0.1  www.onlinewebservice3.de
127.0.0.1  onlybestsex.com #[Win32/Adware.Toolbar.WinThirtyTwo]
127.0.0.1  www.onlybestsex.com
127.0.0.1  onlysex.ws
127.0.0.1  www.onlysex.ws #[Troj/IEStart-F]
127.0.0.1  feed.only-tok-777.com
127.0.0.1  www.onmpeg.com #[Malicious.Links]
127.0.0.1  www.onporn.info #[Spamdexing]
127.0.0.1  www.orgygallery.net
127.0.0.1  www.orray.com #[Spamdexing]
127.0.0.1  orira.info #[Spamdexing][Malicious Links]
# [P]
127.0.0.1  www.pagerank10.co.uk
127.0.0.1  banners.paneuromedia.com
127.0.0.1  www.pantyhosecastle.com #[IFrame.Exploit]
127.0.0.1  promotion.partnercash.de
127.0.0.1  party-adult.com
127.0.0.1  www.party-adult.com #[Malicious.Links]
127.0.0.1  promo.passioncams.com
127.0.0.1  access.passwordbyphone.com
127.0.0.1  banners.passwordbyphone.com
127.0.0.1  gfx.passwordbyphone.com
127.0.0.1  interface.passwordbyphone.com
127.0.0.1  www.passwordbyphone.com
127.0.0.1  www.paysefeed.com #[Hayter Merchants Group]
127.0.0.1  banners.payserve.com
127.0.0.1  perfectgirls.net
127.0.0.1  www.perfectgirls.net
127.0.0.1  banners.perfectgonzo.com
127.0.0.1  bannershotlink.perfectgonzo.com
127.0.0.1  www.pergioco.com
127.0.0.1  www.phallosdei.com #[Malicious Links]
127.0.0.1  cache.phazeporn.com
127.0.0.1  cartoon.photoswold.com
127.0.0.1  black.photoswold.com
127.0.0.1  tits.photoswold.com #[IFrame.Exploit]
127.0.0.1  php4you.biz
127.0.0.1  picsandmovs.com #[Trojan.Codec]
127.0.0.1  www.picsandmovs.com
127.0.0.1  pimp21.com #[IFrame.Exploit]
127.0.0.1  www.pimp21.com
127.0.0.1  error.pimproll.com
127.0.0.1  pinkcount.com
127.0.0.1  www.pinkcount.com
127.0.0.1  pinkteeens.com #[Malicious.Links.Codec]
127.0.0.1  pinkteentop.com #[IFrame.Exploit]
127.0.0.1  pink-top.com #[IFrame.Exploit]
127.0.0.1  www.pinkyellow.com
127.0.0.1  pixyoung.com #[Javascript.Exploit]
127.0.0.1  pei-ads.playboy.com #[RealMedia]
127.0.0.1  play-movie.net #[Malicious Links]
127.0.0.1  www.play-movie.net
127.0.0.1  www.play-porn.net
127.0.0.1  ads.pno.net
127.0.0.1  prettygirlsgames.com
127.0.0.1  www.prettygirlsgames.com #[Javascript.Exploit][server down?]
127.0.0.1  prodtraffic.com
127.0.0.1  pooorrrnoo.com #[VideosCash]
127.0.0.1  www.porn2world.com
127.0.0.1  pornavigator.net
127.0.0.1  www.pornavigator.net
127.0.0.1  my.porn-info.info #[Spamdexing]
127.0.0.1  www.porncash.de
127.0.0.1  ads.porncash.tv
127.0.0.1  www.porncash.tv
127.0.0.1  porncategory.com #[Trojan.Codec]
127.0.0.1  www.porncategory.com
127.0.0.1  pornclips4free.com
127.0.0.1  www.pornclips4free.com #[Trojan.Codec]
127.0.0.1  porndigital.net
127.0.0.1  www.porndigital.net #[Malicious.Links]
127.0.0.1  chubbywife.porn-host.org #[Malicious.Links]
127.0.0.1  bearsxxx.porn-host.org #[HTML/TrojanDownloader.XXXToolbar]
127.0.0.1  pornlandz.com #[Adware.EasySearch][Exploit-MhtRedir.gen]
127.0.0.1  www.pornmail.com #[CrackedEarth]
127.0.0.1  porns-master.com #[Malicious Links]
127.0.0.1  porn0site.org #[Malicious Links]
127.0.0.1  pornoplane.com
127.0.0.1  www.pornrose.com #[Google Warning]
127.0.0.1  pornoteeny.net #[Malicious Links]
127.0.0.1  pornthum.com
127.0.0.1  www.power-counter.com
127.0.0.1  redirect.pr0-search.biz
127.0.0.1  ads.privatefeeds.com
127.0.0.1  protect-x.com
127.0.0.1  www.psbbanners.com
127.0.0.1  www.psysearch.biz #[Videoscash]
127.0.0.1  puadre.info #[Videoscash]
127.0.0.1  banners.publipagos.com
127.0.0.1  pumpherhump.com #[Malicious Links]
127.0.0.1  purefuck.com
127.0.0.1  ads.purefuck.com
127.0.0.1  pussybabes.net
127.0.0.1  www.pussybabes.net
127.0.0.1  banners.pythonvideo.com
127.0.0.1  banners2.pythonvideo.com
127.0.0.1  tracker.pythonvideo.com
127.0.0.1  www.pythonpays.com
# [Q]
127.0.0.1  q21.info
127.0.0.1  quickuseronline.com
127.0.0.1  qweufywe.com
# [R]
127.0.0.1  www.ranking-charts.de
127.0.0.1  www.rank-guru.com
127.0.0.1  www.ranking-links.de
127.0.0.1  www.ranksexo.com
127.0.0.1  rare-niches.com
127.0.0.1  www.rare-niches.com #[Malicious.Links]
127.0.0.1  gay.rated100.com
127.0.0.1  relax-site.name #[Spamdexing]
127.0.0.1  redirectx.net #[Malicious.Links]
127.0.0.1  redirweb.info
127.0.0.1  ads.redtube.com
127.0.0.1  hit.reference-sexe.com
127.0.0.1  banners.reginepompinare.com
127.0.0.1  relaxteens.com
127.0.0.1  www.relaxteens.com #[Javascript.Exploit]
127.0.0.1  restraffic.com
127.0.0.1  review-porn.net #[Malicious.Links]
127.0.0.1  www.review-porn.net
127.0.0.1  banners.rexmag.com
127.0.0.1  rainbowdisplays.com #[Spamdexing]
127.0.0.1  roadteens.com
127.0.0.1  www.roadteens.com #[Javascript.Exploit]
127.0.0.1  www.robsxxx.com
127.0.0.1  www.roccomovies.net #[Malicious Links]
127.0.0.1  stats.rhyman.com
# [S]
127.0.0.1  saletraffic.info #[Trojan.Codec]
127.0.0.1  sallegoodbuy.com #[server down?]
127.0.0.1  www.sappypussy.com #[Javascript.Exploit]
127.0.0.1  adserver.saxonsoft.hu
127.0.0.1  adult.scgirls.info #[Trojan.Codec]
127.0.0.1  sex.scgirls.info
127.0.0.1  sex.scgirls.org #[Malicious.Links.Zango]
127.0.0.1  www.scgirls.org
127.0.0.1  schoolboysite.com #[Javascript.Exploit]
127.0.0.1  www.screamingvideos.com
127.0.0.1  screengirls.net #[Trojan.Codec]
127.0.0.1  www.screengirls.net
127.0.0.1  seaarch.info #[Spamdexing]
127.0.0.1  search4us.us
127.0.0.1  search-q.com
127.0.0.1  searchadult.info
127.0.0.1  st.seblg.com #[Spamdexing]
127.0.0.1  selectpornvids.com
127.0.0.1  www.selectpornvids.com #[Videoscash]
127.0.0.1  www.seo1.org #[JS/Exploit.MS05-013]
127.0.0.1  www.r.seolog.net #[Spamdexing]
127.0.0.1  www.seolog.net
127.0.0.1  seosfive.info
127.0.0.1  find.server4hosting.info
127.0.0.1  lolita.server4hosting.info #[Spamdexing]
127.0.0.1  portal.server4hosting.info
127.0.0.1  videos.server4hosting.info #[Videoscash]
127.0.0.1  www.sessosubito.net
127.0.0.1  titsbrew.sex2inc.com #[IFrame.Exploit]
127.0.0.1  imageads.sexmoney.com
127.0.0.1  sexandmovie.com #[Malicious Links]
127.0.0.1  www.sexandmovie.com #[Javascript.Exploit]
127.0.0.1  www.sexas.us
127.0.0.1  ad.sexcount.de
127.0.0.1  www.sexcount.de
127.0.0.1  adv.sexcounter.com #[Ewido.TrackingCookie.Sexcounter]
127.0.0.1  cs.sexcounter.com #[Panda.Spyware:Cookie/cs.sexcounter]
127.0.0.1  sexcox.net #[Malicious.Links.drivecleaner.com]
127.0.0.1  sexempire.biz #[Malicious.Links]
127.0.0.1  www.sexempire.biz
127.0.0.1  www.sexhit.com
127.0.0.1  freeporn.sexhooonline.com #[Spamdexing]
127.0.0.1  www.sexhooonline.com
127.0.0.1  www.sexleech.com
127.0.0.1  click.sexmoney.com
127.0.0.1  pagepeels.sexmoney.com
127.0.0.1  www.sexmoney.com
127.0.0.1  bannerrotation.sexmoney.com
127.0.0.1  sex-sexurity.com #[Malicious Links]
127.0.0.1  www.sex-to-er.info #[Spamdexing]
127.0.0.1  sexplanet.name #[Malicious Links]
127.0.0.1  www.sexproper.com #[Malicious Links]
127.0.0.1  banners.sexsearch.com
127.0.0.1  textad.sexsearch.com
127.0.0.1  wt.sexsearchcom.com #[WebTrends]
127.0.0.1  counter.sexsuche.tv
127.0.0.1  banner.sextorrent.to
127.0.0.1  www.sextriere.com #[Malicious.Links.Zango]
127.0.0.1  sexualblondes.net
127.0.0.1  www.sexualblondes.net
127.0.0.1  sexvideostation.info #[Javascript.Exploit][server down?]
127.0.0.1  www.sex-watch.com
127.0.0.1  sex-sex-web.com #[IFrame.Exploit]
127.0.0.1  www.sexxxpass.com #[SecurityRisk.SexxPass]
127.0.0.1  members.sexroulette.com
127.0.0.1  wts.sexrouter.net
127.0.0.1  hestia.sextrail.com
127.0.0.1  sexy-access.com #[Malicious.Links]
127.0.0.1  www.sexy-access.com
127.0.0.1  reseller.sexyads.com
127.0.0.1  sexy-and-hot.com #[Malicious Links]
127.0.0.1  sexyfamouscelebs.com #[Javascript.Exploit]
127.0.0.1  www.sexyfamouscelebs.com
127.0.0.1  www.sexylux.com #[McAfee.StartPage-IF]
127.0.0.1  sexymomss.com #[IFrame.Exploit]
127.0.0.1  legs.sexymomss.com
127.0.0.1  www.sexymomss.com
127.0.0.1  logs.sexy-parade.com
127.0.0.1  sexyteen-pictures.com #[Malicious Links]
127.0.0.1  sexyteenspix.com #[Malicious.Links.Codec]
127.0.0.1  www.sexyteenspix.com
127.0.0.1  sexytraffic.info #[Spamdexing]
127.0.0.1  sexy-vids.info #[Malicious Links]
127.0.0.1  sexyoung.us
127.0.0.1  www.sexysportschicks.com #[Malicious.Links.Zango]
127.0.0.1  www.shinypics.com
127.0.0.1  shock-bbs.com #[Malicious.Links]
127.0.0.1  www.shockingtheworld.com #[Malicious.Links]
127.0.0.1  link.siccash.com
127.0.0.1  www.siliconboys.info #[Spamdexing]
127.0.0.1  click.silvercash.com
127.0.0.1  exit.silvercash.com
127.0.0.1  smc.silvercash.com
127.0.0.1  www.silvercash.com #[SiteAdvisor.silvercash.com]
127.0.0.1  simple-buy.net #[Spamdexing]
127.0.0.1  sinnak.com #[Spamdexing][server down?]
127.0.0.1  www.slackernetwork.com #[Malicious Links]
127.0.0.1  stats.smartbucks.com
127.0.0.1  smashingvids.com
127.0.0.1  www.smashingvids.com #[Malicious.Links.Codec]
127.0.0.1  www.smokyvids.com #[Javascript.Exploit]
127.0.0.1  ad.smsmovies.net
127.0.0.1  ad.smsmovie.tv
127.0.0.1  www.smutbeach.com #[Trojan.Codec]
127.0.0.1  www.sockshots.com #[Malicious.Content.Zango]
127.0.0.1  soft-911.com #[Malicious.Links]
127.0.0.1  www.soft-911.com
127.0.0.1  counters.soft-com.biz
127.0.0.1  amare.softwaregarden.com #[Win32/TrojanDownloader.Small.AWA]
127.0.0.1  sparesex.info #[Spamdexing]
127.0.0.1  special-movies.com #[Malicious Links]
127.0.0.1  spunkyvids.com
127.0.0.1  www.spunkyvids.com #[Malicious.Links.Codec]
127.0.0.1  banners.solocazzienormi.com
127.0.0.1  www.splem.net
127.0.0.1  www.spycamvideo.net #[Win32/Dialer.QI]
127.0.0.1  ds.starmedia.com
127.0.0.1  stat1count.net #[Javascript.Exploit][Google Warning]
127.0.0.1  statsgold.com
127.0.0.1  strcontrol.com
127.0.0.1  banners.images.streamray.com
127.0.0.1  www.stockingssite.com #[Malicious.Links]
127.0.0.1  www.stockway.net #[Spamdexing]
127.0.0.1  new.stylishvideo.com #[Malicious.Links]
127.0.0.1  banners.sublimedirectory.com
127.0.0.1  summervids.com
127.0.0.1  www.summervids.com #[IFrame.Exploit]
127.0.0.1  sunlovegalz.com #[IFrame.Exploit]
127.0.0.1  www.sunnygals.com #[Spamdexing]
127.0.0.1  landingpages.sunnytoolz.com
127.0.0.1  superadultfriend.com
127.0.0.1  superfastsservers.com #[Spamdexing]
127.0.0.1  www.superfastsservers.com
127.0.0.1  supergirlz.info
127.0.0.1  supersexpass.com #[SunBelt.SuperSexPass]
127.0.0.1  www.supersexpass.com
127.0.0.1  www.sexwetporn.org #[Malicious.Links]
127.0.0.1  www.swevc.com #[Malicious.Links]
127.0.0.1  www.swingerhotcams.com
# [T]
127.0.0.1  t3mortgage.com
127.0.0.1  takoe.org #[Spamdexing]
127.0.0.1  tankvids.com #[Javascript.Exploit]
127.0.0.1  www.tankvids.com #[Javascript.Exploit]
127.0.0.1  ads.tarrobads.com
127.0.0.1  taxfreesex.com #[Videoscash]
127.0.0.1  www.taxfreesex.com
127.0.0.1  tds7.info #[Videoscash]
127.0.0.1  www.tds69.com #[Malicious Links]
127.0.0.1  teenfuckinsite.com #[Malicious.Links]
127.0.0.1  www.teenfuckinsite.com
127.0.0.1  teenhost.net #[MHTMLRedir.Exploit]
127.0.0.1  www.teenhost.net
127.0.0.1  banners.teeniemovies.com
127.0.0.1  www.teenshardvideos.com #[IFrame.Exploit]
127.0.0.1  teenhotpix.com
127.0.0.1  www.teenhotpix.com #[IFrame.Exploit]
127.0.0.1  teenlemon.com #[IFrame.Exploit]
127.0.0.1  teens24h.com
127.0.0.1  www.teensaround.com #[Javascript.Exploit]
127.0.0.1  www.teenschicks.com
127.0.0.1  teensexdot.com #[Malicious.Links]
127.0.0.1  teens.teenssites.net
127.0.0.1  teens-girls.org
127.0.0.1  th.teens-girls.org #[Trojan.Codec]
127.0.0.1  www.teens-girls.org #[Google Warning]
127.0.0.1  teenshardvideos.com #[IFrame.Exploit]
127.0.0.1  www.teensinlaw.com #[Javascript.Exploit]
127.0.0.1  teensmoreteens.com
127.0.0.1  www.teensmoreteens.com #[Malicious Links]
127.0.0.1  www.teenpalacetgp.info #[Malicious Links]
127.0.0.1  teensparty.net #[Videoscash]
127.0.0.1  www.teenporn18.eu #[Malicious Links]
127.0.0.1  www.teensparty.net
127.0.0.1  www.teensales.com
127.0.0.1  teenssex.info #[Google Warning]
127.0.0.1  teentop.biz #[IFrame.Exploit]
127.0.0.1  teentop.org #[Malicious.Links]
127.0.0.1  teen-zonex.com
127.0.0.1  www.teen-zonex.com #[W32/Dialer.gen]
127.0.0.1  teyzemx.info #[Malicious.Links]
127.0.0.1  www.tgp69.info #[Malicious Links]
127.0.0.1  tgptraffictrades.com
127.0.0.1  thebugs.ws #[Trojan.Win32.StartPage.fg]
127.0.0.1  img.thebugs.ws
127.0.0.1  www.thebugs.ws #[Trojan.Favadd]
127.0.0.1  thefattygirl.org
127.0.0.1  thefreenude.com
127.0.0.1  thehan.net
127.0.0.1  the-hard-movies.com #[IFrame.Exploit]
127.0.0.1  www.thehon.com
127.0.0.1  www.thehun.com #[Win32.Lospad.B]
127.0.0.1  thehun.net
127.0.0.1  www.thehun.net
127.0.0.1  banner.thenudelist.com
127.0.0.1  thesesso.info #[Spamdexing]
127.0.0.1  www.thesexcinema.com #[McAfee.Cookie-TheSexCinema]
127.0.0.1  theteenxxx.com #[IFrame.Exploit]
127.0.0.1  www.theteenxxx.com
127.0.0.1  thetraff.com
127.0.0.1  www.theyahoomusic.org #[Javascript.Exploit][server down?]
127.0.0.1  thirdritual.com
127.0.0.1  www.thirdritual.com #[IFrame.Exploit][Google Warning]
127.0.0.1  www.thumbuka.com #[IFrame.Exploit]
127.0.0.1  www.thunder-ball.net
127.0.0.1  tiny-babes.net
127.0.0.1  tntteens.com #[IFrame.Exploit]
127.0.0.1  www.todayshunks.com #[Malicious.Links.Zango]
127.0.0.1  www.todoporn.com #[Malicious.Links]
127.0.0.1  www.toples.org #[Malicious.Links]
127.0.0.1  to-porn.com #[Spamdexing][Videoscash]
127.0.0.1  top11.ru
127.0.0.1  counter.top.dating.lt
127.0.0.1  toppornclips.com #[Videoscash]
127.0.0.1  www.toppornclips.com
127.0.0.1  www.top-porn-sites.info
127.0.0.1  top-secret-sex.com #[Malicious.Links]
127.0.0.1  images.top66.ro
127.0.0.1  script.top66.ro
127.0.0.1  www.top66.ro
127.0.0.1  www.topsites24.de
127.0.0.1  top-whores.com #[IFrame.Exploit]
127.0.0.1  www.top-whores.com
127.0.0.1  www.tossoffads.com
127.0.0.1  www.trafficadept.com
127.0.0.1  www.trafficrank.de
127.0.0.1  www.traffoman.com #[Spamdexing]
127.0.0.1  trafredirector.info
127.0.0.1  traffcommunity.com
127.0.0.1  trafficroup.com #[Malicious.Links]
127.0.0.1  thumb.trafficroup.com
127.0.0.1  www.traffic-trades.com
127.0.0.1  clicks.traffictrader.net
127.0.0.1  clicks2.traffictrader.net
127.0.0.1  clicks3.traffictrader.net
127.0.0.1  clicks.eutopia.traffictrader.net
127.0.0.1  hestia.sextrail.trakkerd.net
127.0.0.1  www.triplexcounter.com
127.0.0.1  affiliates.thrixxx.com
127.0.0.1  content.thrixxx.com
127.0.0.1  adds.trafflow.com
127.0.0.1  freeimghost.trafflow.com #[Spamdexing]
127.0.0.1  troiegratis.net
127.0.0.1  www.troiegratis.net
127.0.0.1  troietta.com
127.0.0.1  www.troietta.com
127.0.0.1  tropezitalia.com #[McAfee.Downloader-AVT]
127.0.0.1  banner.tropezitalia.com #[Adware.Casino]
127.0.0.1  www.tropezitalia.com #[Malicious.Links]
127.0.0.1  troyterafirma.com #[Spamdexing]
127.0.0.1  www.troyterafirma.com
127.0.0.1  truebbw.net #[Google.Warning]
127.0.0.1  banners.truecash.com
127.0.0.1  tv69.com
127.0.0.1  streaming.tv69.com
127.0.0.1  www.tv69.com #[JS/NoClose-G]
127.0.0.1  twinklane.com
127.0.0.1  www.twinklane.com #[Malicious Links]
# [U]
127.0.0.1  unisearch.name #[Spamdexing]
127.0.0.1  content.unisearch.name
127.0.0.1  freecounter.unms.com
127.0.0.1  unrealmature.com #[Videoscash]
127.0.0.1  www.unrealmature.com #[Google Warning]
127.0.0.1  www.uncensored-sex.org #[Malicious.Links]
127.0.0.1  us-team.us #[Malicious.Links]
# [V]
127.0.0.1  vaccinome.com #[Spamdexing]
127.0.0.1  www.vaccinome.com
127.0.0.1  best-sellers.vegnews.com
127.0.0.1  consultive.vegnews.com
127.0.0.1  glo.vegnews.com
127.0.0.1  lance.vegnews.com #[Win32/TrojanDownloader.Small.AWA]
127.0.0.1  margara.vegnews.com
127.0.0.1  ads.velcom.com
127.0.0.1  video-clips.in
127.0.0.1  www.video-clips.in #[Videoscash]
127.0.0.1  www.vids-home.com
127.0.0.1  videohall.info #[Malicious Links][server down?]
127.0.0.1  videomoviesonline.com #[Trojan.Codec]
127.0.0.1  www.videomoviesonline.com #[Malicious.Links]
127.0.0.1  banners.videosz.com
127.0.0.1  videoweststudio.com #[Videoscash]
127.0.0.1  videozfree.com #[Videoscash][Google Warning]
127.0.0.1  www.videozfree.com
127.0.0.1  vidsparade.com #[Malicious.Links]
127.0.0.1  www.viennateens.com #[IFrame.Exploit]
127.0.0.1  vipmpg.net #[Malicious Links]
127.0.0.1  www.virgilio.in #[Malicious.Links.Zango]
127.0.0.1  www.virgins.se #[eTrust.Sex Cams]
127.0.0.1  virginfoto.com #[IFrame.Exploit]
127.0.0.1  virginsplay.com #[IFrame.Exploit]
127.0.0.1  virgins.porno-private.net #[IFrame.Exploit]
127.0.0.1  www.vispateresa.biz #[Win32/TrojanProxy.Agent.LK]
127.0.0.1  vote4me.de
127.0.0.1  vpantyhose.com #[Malicious.Links]
127.0.0.1  www.vpantyhose.com
# [W]
127.0.0.1  www.w3counter.com
127.0.0.1  www.wallpapernudes.com #[Trojan.Codec][cds.zango.com]
127.0.0.1  ads.wanadooregie.com
127.0.0.1  www.warningpages.com
127.0.0.1  www.watchingthetube.com #[Malicious.Links]
127.0.0.1  adserver.weakgame.com
127.0.0.1  promos.wealthymen.com
127.0.0.1  webfreepornmovies.com #[Malicious Links]
127.0.0.1  webhosthit.com
127.0.0.1  websfirst.info
127.0.0.1  www.websfirst.info #[Spamdexing][Videoscash]
127.0.0.1  www.webhostingcounter.com
127.0.0.1  ads.webmasterprofitcenter.com
127.0.0.1  gfx.webmasterprofitcenter.com
127.0.0.1  peel.webmasterprofitcenter.com
127.0.0.1  promo.webmasterprofitcenter.com
127.0.0.1  websitevisitors.net
127.0.0.1  banners.weboverdrive.com
127.0.0.1  web-xxx-video.org #[Malicious.Links]
127.0.0.1  www.wellcams.biz #[Spamdexing]
127.0.0.1  banners.weselltraffic.com
127.0.0.1  clicks.weselltraffic.com
127.0.0.1  feeds.weselltraffic.com
127.0.0.1  www.websitealive3.com
127.0.0.1  webtitan.info #[HTML/TrojanDownloader.Agent.AO]
127.0.0.1  wet-little-pussies.com
127.0.0.1  wetnylons.net #[Videoscash]
127.0.0.1  www.wetnylons.net
127.0.0.1  www.whatpornsite.com #[Backdoor.Nibu.G]
127.0.0.1  www.what-you-want.biz #[Malicious.Links][server down?]
127.0.0.1  www.whoisonline.net
127.0.0.1  www.wickedpictures.com #[Win32/Agent.PA]
127.0.0.1  wild-movies.com
127.0.0.1  www.wild-movies.com #[Videoscash]
127.0.0.1  willywonka.co.in #[Spamdexing]
127.0.0.1  withpornstars.com
127.0.0.1  www.withpornstars.com
127.0.0.1  www.wmsonic.com #[Spamdexing]
127.0.0.1  www.worlddatinghere.com
127.0.0.1  worldofadult.com #[Videoscash][IFrame.Exploit]
127.0.0.1  www.worldporn.in
127.0.0.1  world-sex-pics.com #[Malicious.Links]
127.0.0.1  wpi.biz #[Spamdexing]
127.0.0.1  www.wtfmedia.com
# [X]
127.0.0.1  x9search.com #[Spamdexing]
127.0.0.1  xathzesocc.com #[Malicious.Links]
127.0.0.1  www.xbeta69.com
127.0.0.1  ads.xbiz.com
127.0.0.1  engine.xbiz.com
127.0.0.1  exchange.xbiz.com
127.0.0.1  xbxxrvnyes.com #[JS/TrojanDownloader.Agent.AB]
127.0.0.1  x2.xclicks.net
127.0.0.1  x3.xclicks.net
127.0.0.1  www.xclicks.net
127.0.0.1  www.xeighteen.com #[Malicious.Links.Codec]
127.0.0.1  xexexe.info
127.0.0.1  amour-xxx-angels.xhostar.com #[Malicious.Links]
127.0.0.1  cocovideo.xhostar.com #[IFrame.Exploit]
127.0.0.1  xlocator.com #[PcTools.XLocator]
127.0.0.1  adblocks.xmlscope.net
127.0.0.1  www.xlocator.com #[HJTH.Xlocator/WinLocator Adware]
127.0.0.1  www.x-orgy.com #[IFrame.Exploit]
127.0.0.1  r.x-pictures.org #[Spamdexing]
127.0.0.1  xpictx.com #[under-xxx.com]
127.0.0.1  x-road.co.kr
127.0.0.1  www.xsex.ws #[Troj/IEStart-F]
127.0.0.1  www.xstat.pl
127.0.0.1  a1.x-traceur.com
127.0.0.1  a3.x-traceur.com
127.0.0.1  a12.x-traceur.com
127.0.0.1  a18.x-traceur.com
127.0.0.1  a20.x-traceur.com
127.0.0.1  logos.x-traceur.com
127.0.0.1  services.x-traceur.com
127.0.0.1  www.xtoplist.com #[Malicious.Links.Zango]
127.0.0.1  www.xtporn.com #[Trojan.Codec]
127.0.0.1  zero.xujace.com #[Javascript.Exploit]
127.0.0.1  www.xxx-banner.com
127.0.0.1  nm.xxxeuropean.com
127.0.0.1  www.xxx-exits.com
127.0.0.1  xxx-galleries.info #[Videoscash]
127.0.0.1  stats.xxxkey.com
127.0.0.1  xxxmaidens.com
127.0.0.1  www.xxxmaidens.com #[Videoscash]
127.0.0.1  xxxnrg.com
127.0.0.1  www.xxxnrg.com #[IFrame.Exploit]
127.0.0.1  nudist.xxx-pics.biz #[Videoscash]
127.0.0.1  teen.xxx-pics.biz
127.0.0.1  xxxporncafe.com #[Malicious.Links]
127.0.0.1  xxxpornonline.net #[Malicious.Links]
127.0.0.1  www.xxxpornonline.net
127.0.0.1  xxxreactor.com
127.0.0.1  xxx-trailer.com #[Videoscash]
127.0.0.1  bannerlink.xxxtreams.com
127.0.0.1  www.xxx-trailer.com #[Videoscash]
127.0.0.1  xxx-vid-777.info #[Malicious.Links]
127.0.0.1  xxx-video-clips.org
127.0.0.1  xxxvideossite.com
127.0.0.1  www.xxxvideossite.com #[Videoscash]
127.0.0.1  stats.xxxrewards.com
127.0.0.1  xxxvogue.net #[Trojan.Ruindem]
127.0.0.1  www.xxxvogue.net
127.0.0.1  www.x-stasy.com #[C2Media/LOP variant]
127.0.0.1  xxxxxx.name #[Malicious.Links]
127.0.0.1  benjamin.xww.de #[W32/Kazoa.B]
127.0.0.1  voyour-cams.xww.de #[W32.DSS.Trojan]
# [Y]
127.0.0.1  counter.yakcash.com
127.0.0.1  yap-teens.com #[IFrame.Exploit]
127.0.0.1  ygsondheks.info
127.0.0.1  www.ygsondheks.info #[IFrame.Exploit]
127.0.0.1  ads.ynot.com
127.0.0.1  youngteenmodel.info #[Trojan.Codec]
127.0.0.1  yourteensgalleries.info #[Javascript.Exploit]
127.0.0.1  yourthumbnails.com #[IFrame.Exploit]
127.0.0.1  www.yourthumbnails.com #[Exploit.WMF]
127.0.0.1  yourjizz.com #[Malicious.Links]
127.0.0.1  www.yourjizz.com
127.0.0.1  www.yukselt.net #[Exploit.PsyBotInstaller]
127.0.0.1  www.yummyclips.com #[Malicious.Links]
# [Z]
127.0.0.1  zalupa.net
127.0.0.1  zbiornik.com
127.0.0.1  redirect.zbestservice.info #[Malicious.Links.Codec]
127.0.0.1  zdrqmpad.com #[Javascript.Exploit]
127.0.0.1  zetincest.com #[Malicious.Links]
127.0.0.1  zooclips.net #[Malicious.Links][server down?]
127.0.0.1  www.zooclips.net
127.0.0.1  zoo-cum.com
127.0.0.1  zr0.net
127.0.0.1  ztabros66.info #[Malicious.Links]
127.0.0.1  banners.ztod.com
127.0.0.1  zvids.com #[Malicious Links]
127.0.0.1  www.zvids.com
# [24 interactive]
127.0.0.1  campaigns.de.euserv.adaos-ads.net
127.0.0.1  cpx.v1.de.euserv.adaos-ads.net
127.0.0.1  img.v1.de.euban.adaos-ads.net
127.0.0.1  js.v1.de.euserv.adaos-ads.net
127.0.0.1  mailserv.v1.de.euserv.adaos-ads.net
127.0.0.1  static.de.euserv.adaos-ads.net
127.0.0.1  viewcount.v1.de.euserv.adaos-ads.net
# [Adult Webmaster Dream]
127.0.0.1  awm-dream.com #[Parasite.CoolWebSearch.InternetMgr]
127.0.0.1  teens-dream.com
127.0.0.1  www.teens-dream.com
127.0.0.1  web-searcher.info
# [AdWorld Media Corp]
127.0.0.1  ads.adultadworld.com
127.0.0.1  ads3.adultadworld.com
127.0.0.1  ads6.adultadworld.com
127.0.0.1  cluster.adultadworld.com
127.0.0.1  hippo.adultadworld.com
127.0.0.1  newt1.adultadworld.com
127.0.0.1  partners.adultadworld.com
127.0.0.1  textads.adultadworld.com
127.0.0.1  tigershark.adultadworld.com
127.0.0.1  eroticlick.net
127.0.0.1  www.eroticlick.net #[Malicious Links]
# [Alexander the Great]
127.0.0.1  adultgayvideo.net
127.0.0.1  anamateur.net
127.0.0.1  andpornomovies.com #[Google.Warning]
127.0.0.1  adult-toon.net
127.0.0.1  bbwlibrary.net #[SiteAdvisor.bbwlibrary.net]
127.0.0.1  bdsmorgy.net
127.0.0.1  best4all.net
127.0.0.1  bigboobsmovies.info
127.0.0.1  blowjobsmovies.net
127.0.0.1  everymatures.com
127.0.0.1  excitingfetish.net
127.0.0.1  fetishvideoclips.net
127.0.0.1  freeanalvideo.net
127.0.0.1  freebbwmovies.net
127.0.0.1  free-babies.com
127.0.0.1  freebigboobs.info #[IFrame.Exploit]
127.0.0.1  img.freebigboobs.info
127.0.0.1  free-cutie.com
127.0.0.1  freeebonymovies.net
127.0.0.1  free-guy-movie.com
127.0.0.1  free-mature-videos.net
127.0.0.1  free-voyeur-video.net
127.0.0.1  fuckinggay.net
127.0.0.1  gaysportal.net
127.0.0.1  hardcorebook.net
127.0.0.1  hotpornflow.net
127.0.0.1  maturepass.net
127.0.0.1  maturesexmovies.info
127.0.0.1  maturestime.net
127.0.0.1  no1sex.net
127.0.0.1  onlinesexmovie.net
127.0.0.1  orgygalleries.net
127.0.0.1  img.orgygalleries.net
127.0.0.1  www.orgygalleries.net
127.0.0.1  pornmoviesfree.net
127.0.0.1  promogals.com
127.0.0.1  sexasianvideo.net
127.0.0.1  sexlesbianmovies.com
127.0.0.1  straightgay.net
127.0.0.1  teendvdmovies.info
127.0.0.1  topmatures.net
127.0.0.1  trannysvideos.com
127.0.0.1  xxxamateurvideo.net
127.0.0.1  xxxteensfree.com
# [Aleksei Beljajev Group]
127.0.0.1  boytgp.net
127.0.0.1  www.boytgp.net
127.0.0.1  hotvideofiles.com #[Google.Warning]
127.0.0.1  www.hotvideofiles.com
127.0.0.1  king-clips.com #[IFrame.Exploit]
127.0.0.1  www.king-clips.com
127.0.0.1  www.madresources.com
127.0.0.1  schoolgayboy.com
127.0.0.1  www.schoolgayboy.com
127.0.0.1  sexymomvid.info
127.0.0.1  www.sexymomvid.info
127.0.0.1  twinksmovies.us
127.0.0.1  www.twinksmovies.us
127.0.0.1  unlimitedgays.com #[SiteAdvisor.unlimitedgays.com]
127.0.0.1  www.unlimitedgays.com
127.0.0.1  youngerboys.us #[Google.Warning]
# [AndersonWebConsulting]
127.0.0.1  easy-search.biz #[Adware.EasySearch]
127.0.0.1  worldtracker.biz #[Adware.EasySearch][Troj/Small-PU]
# [Andre Agnoletto][Adware.CtxPopup]
127.0.0.1  brdatahost.com #[Troj/Agent-FZ]
# [Angel Mol]
127.0.0.1  freehqmovies.com #[yeahsearch.net]
127.0.0.1  www.freehqmovies.com #[SunBelt.FreeHQMovies]
127.0.0.1  teeniedialer.com #[SunBelt.TeenieDialer]
127.0.0.1  www.teeniedialer.com #[yeahsearch.net]
# [Antonio Kapunes]
127.0.0.1  hugevideohost.com
127.0.0.1  newvideogalleries.com #[Trojan.Codec][Trojan.Win32.Obfuscated.ev]
127.0.0.1  pornvideos2007.com
127.0.0.1  worldmoviehost.com
# [APC Entertainment][CAN-SPAM Act]
127.0.0.1  adultplayersclub.com
127.0.0.1  www.adultplayersclub.com
# [Aligned Acquisitions][Beano Pubishing]
127.0.0.1  authorizedsearchagents.com
127.0.0.1  ebtmarketing.com
127.0.0.1  www.ebtmarketing.com
127.0.0.1  www.freeezinebucks.com #[SiteAdvisor.freeezinebucks.com]
127.0.0.1  freeticketcash.com
127.0.0.1  www.freeticketcash.com
127.0.0.1  www.searchape.com #[Adware.DailyToolbar]
127.0.0.1  www.topsearchdog.com #[Adware.DailyToolbar]
# [Bangbros.com Inc]
127.0.0.1  oxcash.com #[SunBelt.OxCash]
127.0.0.1  clicks2.oxcash.com
127.0.0.1  popup.oxcash.com
127.0.0.1  track.oxcash.com
127.0.0.1  exit.oxcash2.com
# [Big Host LLC][Alex Goldstein]
127.0.0.1  crackway.com
127.0.0.1  www.crackway.com #[Trojan/StartPage.FG]
127.0.0.1  freexxxpages.net
127.0.0.1  img.freexxxpages.net
127.0.0.1  www.freexxxpages.net
127.0.0.1  ****-album.com
127.0.0.1  www.****-album.com
127.0.0.1  mscracks.com #[Troj/Favadd-D][****-access.com]
127.0.0.1  flz.mscracks.com
127.0.0.1  img.mscracks.com
127.0.0.1  www.mscracks.com
# [Brad Shelly]
127.0.0.1  www.bbw-black-porn.com
127.0.0.1  www.bootylist.com #[Malicious Links]
127.0.0.1  www.britneysbookmarks.com
127.0.0.1  www.dollyslist.com #[Google Warning]
127.0.0.1  www.xxxpornfiles.com
# [Brendan Lewis]
127.0.0.1  www.bunnyteens.com
127.0.0.1  www.candythumbs.com
127.0.0.1  www.orangeteen.com
127.0.0.1  www.puppykibble.com
127.0.0.1  www.raimisthumbs.com
127.0.0.1  www.teenbookmark.com #[Dropper.Small.18.AV]
# [blackdor]
127.0.0.1  adultcatalog4u.com #[Malicious.Links]
127.0.0.1  www.adultcatalog4u.com
127.0.0.1  freshpiercing.com #[Spamdexing]
# [Choker Media]
127.0.0.1  www.chickenbanners.com
127.0.0.1  chokertraffic.com #[Malicious Links]
127.0.0.1  new.chokertraffic.com
127.0.0.1  www.chokertraffic.com
127.0.0.1  www.xsex42.com
# [ClearSearch Group]
127.0.0.1  icansearch.net
127.0.0.1  www.icansearch.net
127.0.0.1  luckysearch.net #[CWS.Tapicfg]
127.0.0.1  www.luckysearch.net
127.0.0.1  watchforall.com
127.0.0.1  www.watchforall.com
# [Clive Rand]
127.0.0.1  gotphaze.com #[Win32/Adware.Toolbar.Eztracks]
127.0.0.1  www.gotphaze.com
127.0.0.1  fullxxxmovies.net
127.0.0.1  www.fullxxxmovies.net #[Videoscash]
# [Crazy Protocol]
127.0.0.1  ads.adultcash.com
127.0.0.1  exits.adultcash.com
127.0.0.1  exits2.adultcash.com
127.0.0.1  home.adultcash.com
127.0.0.1  popfree.adultcash.com
127.0.0.1  www.adultcash.com
127.0.0.1  www.cheatingromance.com
127.0.0.1  www.crazyprotocol.com
127.0.0.1  www.lonelycheatingwives.com
# [Crutop][Alexander Morozov]
127.0.0.1  e.cpa4.org #[W32/PFV-Exploit.A]
127.0.0.1  m.cpa4.org #[MHTMLRedir.Exploit]
127.0.0.1  rc.cpa4.org
127.0.0.1  se-a.cpa4.org
127.0.0.1  se-a.cpa4.net
# [CWIE LLC]
127.0.0.1  bill.ccbill.com
127.0.0.1  images.ccbill.com
127.0.0.1  refer.ccbill.com #[SpySweeper.Spy.Cookie]
127.0.0.1  www.ccbill.com #[Panda.Spyware:Cookie/Ccbill]
127.0.0.1  www.ccbillcs.com
127.0.0.1  www.ccbilleu.com
127.0.0.1  processor.netmgt.com
# [Cyberfuse Technologies]
127.0.0.1  adultplex.com
127.0.0.1  aff.adultplex.com
127.0.0.1  clicks.adultplex.com
127.0.0.1  dialer.adultplex.com #[wc2.mvl.powerhosting.com]
127.0.0.1  exit.adultplex.com #[wc2.powerhosting.com]
127.0.0.1  images.adultplex.com
127.0.0.1  movies.adultplex.com
127.0.0.1  stats.adultplex.com
127.0.0.1  signup.adultplex.com
127.0.0.1  tgp.adultplex.com
# [D.A. Internet Technologies B.V]
127.0.0.1  fhg.dacash.com
127.0.0.1  galleries.dacash.com
127.0.0.1  users.dacash.com
127.0.0.1  www.dacash.com
127.0.0.1  www.daclick.com
127.0.0.1  www.followthislink.org
127.0.0.1  galleries.incestcash.com
127.0.0.1  www.incestcash.com
127.0.0.1  www.realincestvideos.com
# [Danilo Rodrigo]
127.0.0.1  adultfreeware.net
127.0.0.1  www.adultfreeware.net #[TrojanDownloader.Win32.VB.fi]
127.0.0.1  www.fregamnet.com #[McAfee.Adware-AdultBox][TROJ_TL.A]
127.0.0.1  gamentw.com
127.0.0.1  srvfrgm.com
# [EdenCast BV]
127.0.0.1  599.stats.misstrends.com
127.0.0.1  602.stats.misstrends.com
127.0.0.1  604.stats.misstrends.com
127.0.0.1  606.stats.misstrends.com
127.0.0.1  654.stats.misstrends.com
127.0.0.1  671.stats.misstrends.com
127.0.0.1  699.stats.misstrends.com
127.0.0.1  726.stats.misstrends.com
127.0.0.1  750.stats.misstrends.com
127.0.0.1  803.stats.misstrends.com
127.0.0.1  879.stats.misstrends.com
127.0.0.1  1559.stats.misstrends.com
# [Elena Varavva]
127.0.0.1  www.allseek.info #[Trojan/StartPage.FG]
127.0.0.1  anycracks.com #[Trojan.Favadd]
127.0.0.1  bestserials.com #[Troj/Favadd-D]
127.0.0.1  bugsforum.com
127.0.0.1  icracks.net #[Trojan.Win32.Favadd.d]
# [Flying Crocodile]
127.0.0.1  2001positions.com
127.0.0.1  www.flyingcroc.com
127.0.0.1  clicktraq.mtree.com
127.0.0.1  counter.mtree.com
127.0.0.1  dyntraq.mtree.com
127.0.0.1  mtree.com #[Parasite.MoneyTree]
127.0.0.1  mt1.mtree.com
127.0.0.1  mt2.mtree.com
127.0.0.1  mt4.mtree.com #[xxxtoolbar.com]
127.0.0.1  mt10.mtree.com
127.0.0.1  mt12.mtree.com
127.0.0.1  mt32.mtree.com
127.0.0.1  mt37.mtree.com
127.0.0.1  mt55.mtree.com #[Troj/Istbar-BL]
127.0.0.1  mt58.mtree.com
127.0.0.1  mt83.mtree.com
127.0.0.1  mt94.mtree.com
127.0.0.1  mt124.mtree.com #[SiteAdvisor.mtree.com]
127.0.0.1  mt127.mtree.com
127.0.0.1  porn.mtree.com #[Dialer.Moneytree]
127.0.0.1  psy.mtree.com
127.0.0.1  ss.mtree.com
127.0.0.1  the.mtree.com #[SpySweeper.Adware.moneytree]
127.0.0.1  wm.mtree.com #[McAfee.Adware-Nsupdate]
127.0.0.1  xbs.mtree.com #[Downloader.Dyfica.N][Troj/NSUpdate-A]
127.0.0.1  xbs.pao.mtree.com #[TROJ_DYFUCA.X]
127.0.0.1  xbs.sea.mtree.com #[MoneyTree Dialer][SiteAdvisor.mtree.com]
127.0.0.1  www.mtree.com
127.0.0.1  mtreexxx.net
127.0.0.1  freelivesex.cf.mtreexxx.net
127.0.0.1  freeticketcash.cf.mtreexxx.net
127.0.0.1  join4free.cf.mtreexxx.net
127.0.0.1  image2000.mtreexxx.net
127.0.0.1  megaporn.cf.mtreexxx.net
127.0.0.1  xxx.mtreexxx.net
127.0.0.1  www7.mtreexxx.net
127.0.0.1  www.mtreexxx.net #[eTrust.Sex Cams]
127.0.0.1  mtreexxx.nl #[Parasite.MoneyTree]
127.0.0.1  www.mtreexxx.nl #[Troj/NSUpdate-A]
127.0.0.1  banners.outster.com #[SpySweeper.Spy.Cookie]
127.0.0.1  c1.outster.com
127.0.0.1  c2.outster.com #[Panda.Spyware:Cookie/Outster]
127.0.0.1  c3.outster.com
127.0.0.1  clit50.outster.com
127.0.0.1  clit120.outster.com
127.0.0.1  links.outster.com
127.0.0.1  refer1.outster.com
127.0.0.1  refer25.outster.com
127.0.0.1  refer46.outster.com
127.0.0.1  refer85.outster.com
127.0.0.1  refer100.outster.com
127.0.0.1  refer102.outster.com
127.0.0.1  rr1.outster.com
127.0.0.1  start.outster.com
127.0.0.1  stats.outster.com
127.0.0.1  aphrodite.porntrack.com
127.0.0.1  stats1.porntrack.com
127.0.0.1  stats3.porntrack.com
127.0.0.1  ct.sexadnet.com
127.0.0.1  cgi.sexlist.com #[Ewido.TrackingCookie.Sexlist]
127.0.0.1  cgi1.sexlist.com
127.0.0.1  enter.sexlist.com
127.0.0.1  images.sexlist.com
127.0.0.1  links.sexlist.com
127.0.0.1  lobby.sexlist.com #[Panda.Spyware:Cookie/SexList]
127.0.0.1  vis.sexlist.com #[Tenebril.Tracking.Cookie]
127.0.0.1  vis5.sexlist.com
127.0.0.1  xit.sexlist.com #[SunBelt.SexList.com]
127.0.0.1  sextracker.com
127.0.0.1  the.sextracker.com
127.0.0.1  adserver.sextracker.com #[SunBelt.SexTracker.com]
127.0.0.1  banners.sextracker.com
127.0.0.1  counter1.sextracker.com
127.0.0.1  counter2.sextracker.com
127.0.0.1  counter3.sextracker.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  counter4.sextracker.com
127.0.0.1  counter5.sextracker.com
127.0.0.1  counter6.sextracker.com
127.0.0.1  counter7.sextracker.com
127.0.0.1  counter8.sextracker.com
127.0.0.1  counter9.sextracker.com
127.0.0.1  counter10.sextracker.com
127.0.0.1  counter11.sextracker.com
127.0.0.1  counter12.sextracker.com
127.0.0.1  counter13.sextracker.com
127.0.0.1  counter14.sextracker.com
127.0.0.1  counter15.sextracker.com
127.0.0.1  counter16.sextracker.com
127.0.0.1  clit.sextracker.com
127.0.0.1  clit1.sextracker.com #[Tenebril.Tracking.Cookie]
127.0.0.1  clit2.sextracker.com
127.0.0.1  clit3.sextracker.com
127.0.0.1  clit4.sextracker.com
127.0.0.1  clit5.sextracker.com
127.0.0.1  clit6.sextracker.com
127.0.0.1  clit7.sextracker.com
127.0.0.1  clit8.sextracker.com
127.0.0.1  clit9.sextracker.com
127.0.0.1  clit10.sextracker.com
127.0.0.1  clit11.sextracker.com
127.0.0.1  clit12.sextracker.com
127.0.0.1  clit13.sextracker.com
127.0.0.1  clit14.sextracker.com
127.0.0.1  clit15.sextracker.com
127.0.0.1  clit16.sextracker.com
127.0.0.1  elite.sextracker.com
127.0.0.1  graphics1.sextracker.com
127.0.0.1  graphics2.sextracker.com
127.0.0.1  hosting.sextracker.com
127.0.0.1  links.sextracker.com
127.0.0.1  mau.sextracker.com
127.0.0.1  moneytree.sextracker.com
127.0.0.1  ranks.sextracker.com
127.0.0.1  search.sextracker.com
127.0.0.1  start.sextracker.com
127.0.0.1  stats.sextracker.com
127.0.0.1  stx.sextracker.com
127.0.0.1  stx0.sextracker.com
127.0.0.1  stx1.sextracker.com
127.0.0.1  stx2.sextracker.com
127.0.0.1  stx3.sextracker.com
127.0.0.1  stx4.sextracker.com
127.0.0.1  stx5.sextracker.com
127.0.0.1  stx6.sextracker.com
127.0.0.1  stx7.sextracker.com
127.0.0.1  stx8.sextracker.com
127.0.0.1  stx9.sextracker.com
127.0.0.1  stx10.sextracker.com
127.0.0.1  stx11.sextracker.com
127.0.0.1  stx12.sextracker.com
127.0.0.1  stx13.sextracker.com
127.0.0.1  stx14.sextracker.com
127.0.0.1  stx15.sextracker.com
127.0.0.1  stxbans.sextracker.com
127.0.0.1  webmasters.sextracker.com
127.0.0.1  stx.banners.sextracker.com
127.0.0.1  wm.banners.sextracker.com
127.0.0.1  www.sextracker.com
127.0.0.1  ads.sexspaces.com
127.0.0.1  streamate.com
127.0.0.1  broadcaster.streamate.com
127.0.0.1  static.gfx.streamate.com
127.0.0.1  www.streamate.com
127.0.0.1  www.streamatelive.com
127.0.0.1  www.streamsexcam.com #[Spamdexing]
127.0.0.1  c1.xxxcounter.com #[SunBelt.XXXCounter.com]
127.0.0.1  c2.xxxcounter.com
127.0.0.1  c3.xxxcounter.com
127.0.0.1  free.xxxcounter.com
127.0.0.1  grafix.xxxcounter.com
127.0.0.1  links.xxxcounter.com
127.0.0.1  rr1.xxxcounter.com
127.0.0.1  start.xxxcounter.com
# [Francois Pare]
127.0.0.1  asexvideo.com #[McAfee.Spam-YFakeAccount]
127.0.0.1  www.asexvideo.com
127.0.0.1  mcclient.com
# [FriendFinder Inc.]
127.0.0.1  adultfriendfinder.com #[McAfee.Cookie-Adultfriend]
127.0.0.1  ads.adultfriendfinder.com #[SpySweeper.Spy.Cookie][a841.x.akamai.net]
127.0.0.1  adserver.adultfriendfinder.com
127.0.0.1  banners.adultfriendfinder.com
127.0.0.1  cover9.adultfriendfinder.com
127.0.0.1  guest.adultfriendfinder.com
127.0.0.1  iframe.adultfriendfinder.com #[McAfee.Adware-Redalert]
127.0.0.1  option9.adultfriendfinder.com
127.0.0.1  tgp.adultfriendfinder.com #[cams.com]
127.0.0.1  www.adultfriendfinder.com #[Troj/Small-AG][Adware-Adroar.dll]
127.0.0.1  ads.alt.com
127.0.0.1  banners.alt.com
127.0.0.1  ads.amigos.com
127.0.0.1  banners.amigos.com
127.0.0.1  ads.asiafriendfinder.com
127.0.0.1  adserver.asiafriendfinder.com #[banners.friendfinder.com]
127.0.0.1  banners.asiafriendfinder.com
127.0.0.1  www.cyberzine.com #[PcTools.CamGirlsLive ToolBar]
127.0.0.1  ads.friendfinder.com #[a841.x.akamai.net]
127.0.0.1  banners.friendfinder.com
127.0.0.1  e89.friendfinder.com
127.0.0.1  ads.jewishfriendfinder.com
127.0.0.1  banners.gayfriendfinder.com
127.0.0.1  banners.germanfriendfinder.com
127.0.0.1  ads.outpersonals.com #[a841.x.akamai.net]
127.0.0.1  adserver.outpersonals.com #[banners.friendfinder.com]
127.0.0.1  banners.outpersonals.com
127.0.0.1  ads.passion.com #[a841.x.akamai.net]
127.0.0.1  adserver.passion.com
127.0.0.1  banner.passion.com
127.0.0.1  banners.passion.com
127.0.0.1  ads.seniorfriendfinder.com
127.0.0.1  adserver.seniorfriendfinder.com
127.0.0.1  banners.seniorfriendfinder.com
# [George Evergreen]
127.0.0.1  e-orgasm.org
127.0.0.1  www.e-orgasm.org #[Videoscash]
127.0.0.1  erotica-deluxe.com
127.0.0.1  www.erotica-deluxe.com #[Videoscash]
127.0.0.1  gpftt.com #[dollarrevenue.com]
127.0.0.1  www.gpftt.com
# [Hans-Ingvar Hansson][Domännamn Inv]
127.0.0.1  www.10000host.org
127.0.0.1  www.123content.com
127.0.0.1  www.6host.org
127.0.0.1  41298.www1.elwisp.com
127.0.0.1  69360.www1.elwisp.com #[Wildcard DNS]
127.0.0.1  epl.www2.elwisp.com #[Trojan-Downloader.Win32.Small.afa]
127.0.0.1  540.filost.com
127.0.0.1  www.filost.com
127.0.0.1  www.free6.se #[HJTH.Adult Dialer]
127.0.0.1  www.fuckhost.org
127.0.0.1  gnura.com #[HJTH.Adult Dialer]
127.0.0.1  www.gnura.com
127.0.0.1  www7.logih.com #[eTrust.Win32/Pomelo]
127.0.0.1  www.hotel6.net
127.0.0.1  205.www1.p0rt2.com
127.0.0.1  1047.www1.p0rt2.com
127.0.0.1  1866.www1.p0rt2.com
127.0.0.1  11968.www1.p0rt2.com
127.0.0.1  22022.www1.p0rt2.com
127.0.0.1  24419.www1.p0rt2.com
127.0.0.1  27242.www1.p0rt2.com
127.0.0.1  41363.www1.p0rt2.com
127.0.0.1  46498.www2.p0rt2.com #[TR/Dldr.Mediket.DI]
127.0.0.1  49234.www2.p0rt2.com
127.0.0.1  49595.www1.p0rt2.com
127.0.0.1  63138.www1.p0rt2.com #[AdWare.Win32.Mirar.a]
127.0.0.1  65916.www1.p0rt2.com
127.0.0.1  71474.www1.p0rt2.com
127.0.0.1  74204.www1.p0rt2.com
127.0.0.1  79600.www1.p0rt2.com
127.0.0.1  81882.www1.p0rt2.com
127.0.0.1  92654.www1.p0rt2.com
127.0.0.1  95494.www1.p0rt2.com
127.0.0.1  97178.www1.p0rt2.com #[Wildcard DNS]
127.0.0.1  bbdl.www2.p0rt2.com #[MHTMLRedir.Exploit]
127.0.0.1  www.www2.p0rt2.com #[Trojan.Win32.LipGame.i][TR/Dldr.Agen.nv.4.B]
127.0.0.1  www.pornogames.net
127.0.0.1  www.pussyhost.org
127.0.0.1  540.scmg.net
127.0.0.1  www.scmg.net
127.0.0.1  www.sejers.com
# [Hinckley LLC]
127.0.0.1  www.amateurvideopro.com
127.0.0.1  www.analvideopro.com
127.0.0.1  www.bigtitsvideopro.com
127.0.0.1  www.bitchhiking.com
127.0.0.1  www.cashvideopro.com #[otherchance.com]
127.0.0.1  www.gangvideopro.com
127.0.0.1  www.gayvideopro.com
127.0.0.1  www.interracialvideopro.com
127.0.0.1  www.lesbovideopro.com
127.0.0.1  www.sexvideopro.com #[linkautomatici.com]
127.0.0.1  www.teenvideopro.com
127.0.0.1  www.transvideopro.com
# [Holler Enterprises][Adult Tracking Service]
127.0.0.1  exit.xpays.com
127.0.0.1  www.xpays.com
# [ICS Entertainment, Inc]
127.0.0.1  ctc.amateurpages.com
127.0.0.1  clicks.asianamateurpages.com
127.0.0.1  cashtour.com
127.0.0.1  www.cashtour.com
127.0.0.1  ad.erasercash.com #[SunBelt.Erasercash]
127.0.0.1  www.erasercash.com
# [iFrameDollars Group][Ezhi Brozkevitsh]
127.0.0.1  iframedollars.biz #[server down?]
127.0.0.1  iframedollars.com
127.0.0.1  wanrzcvupf.hk
127.0.0.1  wbqkqibkdz.hk
127.0.0.1  wclnsfocxm.hk
127.0.0.1  wdqccrzpmd.hk
127.0.0.1  weyxpwvzer.hk
127.0.0.1  wgrraiqoth.hk
127.0.0.1  whccxpufub.hk
127.0.0.1  xcjqjajpff.com #[JS/TrojanDownloader.Agent.AB]
127.0.0.1  ybbwxlxytz.biz
127.0.0.1  ycsmmiqtyo.biz
127.0.0.1  yaspftqlyr.hk
127.0.0.1  ybdjmiphev.hk #[JS/TrojanDownloader.Agent.AB]
127.0.0.1  ychxrexurx.hk
127.0.0.1  ydqwvsamov.hk #[JS/TrojanDownloader.Agent.AB]
127.0.0.1  yeyjmaoumc.hk
127.0.0.1  yhbcrffjpa.hk
# [Integrated Search Technologies][Gamma Entertainment]
127.0.0.1  activexcash.com
127.0.0.1  www.activexcash.com
127.0.0.1  activexcash.net
127.0.0.1  www.activexcash.net
127.0.0.1  adultgameserver.com
127.0.0.1  www.adultgameserver.com
127.0.0.1  adultgameservers.com
127.0.0.1  www.adultgameservers.com
127.0.0.1  adultmoviemax.com
127.0.0.1  www.adultmoviemax.com
127.0.0.1  couldntfind.com
127.0.0.1  www.couldntfind.com
127.0.0.1  couldnotfind.com
127.0.0.1  www.couldnotfind.com #[TROJ_ISTBAR.AD]
127.0.0.1  www.ebonybymail.com
127.0.0.1  tgp.gammacash.com
127.0.0.1  maximize.gammacash.com
127.0.0.1  stats.gammacash.com
127.0.0.1  www.gammacash.com
127.0.0.1  www.gammasites.com
127.0.0.1  advertising.gammae.com
127.0.0.1  cgi.gammae.com
127.0.0.1  common.gammae.com #[AVG.Dialer.JT]
127.0.0.1  hourly.gammae.com
127.0.0.1  php.gammae.com
127.0.0.1  tracking.gammae.com
127.0.0.1  videostore.gammae.com
127.0.0.1  www.gammaentertainment.com
127.0.0.1  gaysexswap.com
127.0.0.1  cgi.gaysexswap.com
127.0.0.1  www.hardcorebymail.com
127.0.0.1  installcash.com
127.0.0.1  www.installcash.com
127.0.0.1  installdownload.com
127.0.0.1  www.installdownload.com
127.0.0.1  isearchtech.com #[SunBelt.IST.Protector]
127.0.0.1  www.isearchtech.com #[SunBelt.IST.ISTbar]
127.0.0.1  istsvcweb.com
127.0.0.1  www.istsvcweb.com
127.0.0.1  music-lookup.com
127.0.0.1  www.music-lookup.com
127.0.0.1  music-lookup.net
127.0.0.1  www.music-lookup.net
127.0.0.1  pornsearchbar.com
127.0.0.1  www.pornsearchbar.com
127.0.0.1  porntoolbar.com
127.0.0.1  www.porntoolbar.com
127.0.0.1  power-cleaner.com #[McAfee.PowerScan]
127.0.0.1  www.power-cleaner.com
127.0.0.1  www.power-scan.com #[SPYW_POWERSCAN.C]
127.0.0.1  www.safer-scan.com #[Symantec.SaferScan]
127.0.0.1  sexsearchbar.com
127.0.0.1  www.sexsearchbar.com
127.0.0.1  sextoolbar.com
127.0.0.1  www.sextoolbar.com
127.0.0.1  sexswap.com
127.0.0.1  cgi.sexswap.com
127.0.0.1  cgi.sexswap2.com
127.0.0.1  cgi.sexswap2000.com
127.0.0.1  sidefind.com #[Troj/SideFind-A][ADW_SIDEFIND.E]
127.0.0.1  cache.sidefind.com #[McAfee.Adware-ISTbar.dldr]
127.0.0.1  www.sidefind.com #[Adware.SideFind]
127.0.0.1  slidefind.net
127.0.0.1  www.slidefind.net
127.0.0.1  slidesearch.com
127.0.0.1  www.slidesearch.com
127.0.0.1  slidesearch.net
127.0.0.1  www.slidesearch.net
127.0.0.1  slotch.com #[TROJ_ISTBAR.B,K][Trojan.TrustedZones]
127.0.0.1  adult.slotch.com
127.0.0.1  www.slotch.com #[TROJ_ISTBAR.AD][Win32/Adware.Slotch]
127.0.0.1  slotchbar.com #[Troj/IstBar-N]
127.0.0.1  www.slotchbar.com
127.0.0.1  tbcode.com
127.0.0.1  cache.tbcode.com
127.0.0.1  www.tbcode.com #[HJTH.Win32.IstBar.hg]
127.0.0.1  toolbarcash.com #[Parasite.ISTbar]
127.0.0.1  www.toolbarcash.com
127.0.0.1  unlimitedsongs.net
127.0.0.1  www.unlimitedsongs.net
127.0.0.1  xxxtoolbar.com #[Adware.ClickDLoader.B]
127.0.0.1  install.xxxtoolbar.com #[TROJ_ISTBAR.D,I]
127.0.0.1  www.xxxtoolbar.com #[SunBelt.XXXToolBar.com]
127.0.0.1  yoursitebar.com #[Adware.YourSiteBar]
127.0.0.1  rewards.yoursitebar.com
127.0.0.1  stats.yoursitebar.com
127.0.0.1  www.yoursitebar.com #[SPYW_SITEBAR.A]
127.0.0.1  ysbweb.com #[Trojan.TrustedZones][ADW_ISTBAR.K]
127.0.0.1  cache.ysbweb.com #[TROJ_ISTBAR.FN]
127.0.0.1  drm.ysbweb.com #[65181.vidlock.com]
127.0.0.1  www.ysbweb.com #[Win32.Secdrop.AW][TROJ_DLOADER.AIO]
127.0.0.1  www.yyep.com #[searchtraffic.com]
# [IST via Media Traffic][Surfaccuracy][Vomba Network]
127.0.0.1  i-growth.com
127.0.0.1  igrowth.com
127.0.0.1  cpvfeed.mediatraffic.com
127.0.0.1  www.mediatraffic.com
127.0.0.1  mediatrafficagency.com
127.0.0.1  mtagrowth.com
127.0.0.1  www.accuracysurf.com
127.0.0.1  surfaccuracy.com
127.0.0.1  www.surfaccuracy.com #[Adware.SurfAccuracy]
127.0.0.1  surfingaccuracy.com
127.0.0.1  surfingtarget.com
127.0.0.1  surfingtarget.net
127.0.0.1  surfmatch.com
127.0.0.1  vomba.com #[SunBelt.Vomba][Adware.Vomba]
127.0.0.1  www.vomba.com
127.0.0.1  www.vombacash.com
127.0.0.1  www.vombasavers.com
127.0.0.1  vombashots.com #[Adware.Win32.Vomba]
127.0.0.1  www.vombashots.com
127.0.0.1  install.vombanetwork.com #[MVPS.Criteria]
127.0.0.1  services.vombanetwork.com
127.0.0.1  www.vombanetwork.com
# [INNOVATIVE IDEAS]
127.0.0.1  adrevservice.com #[SpySweeper.Spy.Cookie]
127.0.0.1  adult.adrevservice.com
127.0.0.1  stats.adrevservice.com #[Linkzilla Control]
127.0.0.1  www.adrevservice.com #[TROJ_STARTPAG.X]
127.0.0.1  adultrevenueservice.com #[SpySweeper.Spy.Cookie]
127.0.0.1  byot.adultrevenueservice.com
127.0.0.1  counter.adultrevenueservice.com #[Wildcard DNS]
127.0.0.1  counterimg1.adultrevenueservice.com
127.0.0.1  stats.adultrevenueservice.com
127.0.0.1  www.adultrevenueservice.com
127.0.0.1  track.adultdialersolution.com
127.0.0.1  stats.ars4real.com
127.0.0.1  www.arscounter.com
# [Joesh Simonsel]
127.0.0.1  pics-daily.com #[W32.Secefa.C]
# [Jupitermedia Corp][Tracking Service]
127.0.0.1  thecounter.com
127.0.0.1  c1.thecounter.com
127.0.0.1  c2.thecounter.com
127.0.0.1  c3.thecounter.com
127.0.0.1  www.thecounter.com
127.0.0.1  mjxads.internet.com
127.0.0.1  nxads.internet.com
# [Konstantin Popov]
127.0.0.1  www.allpornpics.net
127.0.0.1  www.anal-oral.net
127.0.0.1  gals4you.com
127.0.0.1  www.gals4you.com
127.0.0.1  xrenoder.com
127.0.0.1  cj.xrenoder.com
127.0.0.1  cons.xrenoder.com
127.0.0.1  search.xrenoder.com #[Search.Xrenoder]
127.0.0.1  scripts.xrenoder.com
127.0.0.1  www.xrenoder.com #[CWS.Bootconf]
127.0.0.1  xrenosearch.com
127.0.0.1  www.xrenosearch.com
127.0.0.1  xrenotraf.com
# [Leading Edge Marketing]
127.0.0.1  banners.leadingedgecash.com
127.0.0.1  www2.leadingedgecash.com
127.0.0.1  www.leadingedgecash.com
127.0.0.1  www.albiondrugs.com
127.0.0.1  albionmedical.com
127.0.0.1  www.albionmedical.com
# [Leonard Minter Group]
127.0.0.1  320studio.com #[Videoscash]
127.0.0.1  aesthetic-partners.com
127.0.0.1  alpencors.net #[server down?]
127.0.0.1  www.alpencors.net
127.0.0.1  www.centrointerinale.com
127.0.0.1  www.chiefhosa.com
127.0.0.1  www.dvd-recording.com
127.0.0.1  www.germancenters.com
127.0.0.1  www.highlandmetals.net
127.0.0.1  ibsfc.org
127.0.0.1  i-keman.com #[server down?]
127.0.0.1  kgllc.com #[Videoscash]
127.0.0.1  kmxq.com #[Malicious Links]
127.0.0.1  lasiad.net
127.0.0.1  www.mioco.com
127.0.0.1  misrcities.com
127.0.0.1  mostlyheisey.com
127.0.0.1  piercecountydemocrats.com
127.0.0.1  pinotravel.com #[Videoscash][Spamdexing]
127.0.0.1  postsingularity.com
127.0.0.1  www.robocab.com
127.0.0.1  www.scotty-john.com #[server down?]
127.0.0.1  scjyzb.com #[Trojan.Codec]
127.0.0.1  www.slaterenvirotech.com
127.0.0.1  springbreak2.com
127.0.0.1  www.stff.net
127.0.0.1  www.syscompbelize.com
127.0.0.1  thedocketonline.com
127.0.0.1  vantyz.com #[server down?]
127.0.0.1  woolyboys.com #[Videoscash]
127.0.0.1  www.woolyboys.com
# [Lev Valit][Rtcomm.ru Network Group]
127.0.0.1  andr.net
127.0.0.1  topsites.andr.net
127.0.0.1  www.andr.net
127.0.0.1  www.astabar.com #[AdWare.Win32.Astabar.a]
127.0.0.1  www.astalavista.us
127.0.0.1  justns.com
127.0.0.1  newcracks.net #[Win32.Alcan.C]
127.0.0.1  www.newcracks.net
127.0.0.1  www.porn4free.org
127.0.0.1  serials.ws
127.0.0.1  www.serials.ws
# [Levi Phillips][Hayters Merchants Group]
127.0.0.1  stlinx.info
127.0.0.1  tisall.info #[Trojan.Win32.Obfuscated.ev]
127.0.0.1  zlex.org # [Hayter Merchants Group]
# [liter]
127.0.0.1  fucksuck.biz
127.0.0.1  shock.fucksuck.biz
127.0.0.1  maxporno.biz
127.0.0.1  18.maxporno.biz
127.0.0.1  grand.maxporno.biz
127.0.0.1  tds.maxporno.biz
127.0.0.1  usaporn.org #[MHTMLRedir.Exploit]
127.0.0.1  sex.usaporn.org
# [Mark James]
127.0.0.1  1shemale.org
127.0.0.1  asianscity.com
127.0.0.1  asiapassion.net
127.0.0.1  assland.org
127.0.0.1  babegalleries.org
127.0.0.1  babesvoyeur.net
127.0.0.1  bestmoms.net #[Google.Warning]
127.0.0.1  bigcockland.com #[Malicious.Links]
127.0.0.1  biggay.org
127.0.0.1  www.biggay.org
127.0.0.1  biglargeboobs.net
127.0.0.1  www.biglargeboobs.net
127.0.0.1  bunnytoons.net
127.0.0.1  buttratings.net
127.0.0.1  cumbabes.org #[IFrame.Exploit]
127.0.0.1  cumbusters.net
127.0.0.1  devilshemale.net
127.0.0.1  dullworld.com
127.0.0.1  www.dullworld.com
127.0.0.1  easyvids.com
127.0.0.1  img.easyvids.com
127.0.0.1  www.easyvids.com
127.0.0.1  eroticqueens.com
127.0.0.1  freefat.net
127.0.0.1  freshgirlsporn.com
127.0.0.1  galleryplanet.com
127.0.0.1  gaynaked.net
127.0.0.1  girlsrussian.net
127.0.0.1  hentaiphoto.net
127.0.0.1  hornymature.org
127.0.0.1  hotbigmelons.com
127.0.0.1  hugecockhouse.com #[Javascript.Exploit]
127.0.0.1  hugefatgirl.com
127.0.0.1  juicylesbos.net #[SiteAdvisor.juicylesbos.net]
127.0.0.1  kinkytoons.net
127.0.0.1  lesbians4you.net
127.0.0.1  lovingporn.com #[Javascript.Exploit]
127.0.0.1  img.lovingporn.com
127.0.0.1  mashathumbs.com
127.0.0.1  matureskin.net
127.0.0.1  maturestown.com
127.0.0.1  maturesvid.com #[Google.Warning]
127.0.0.1  www.maturesvid.com
127.0.0.1  momsin.net
127.0.0.1  www.momsin.net
127.0.0.1  www.moneyboobs.com
127.0.0.1  natashathumbs.com
127.0.0.1  ohmature.com
127.0.0.1  www.ohmature.com
127.0.0.1  pantypeaches.net
127.0.0.1  www.pantypeaches.net
127.0.0.1  pornstarocean.com
127.0.0.1  rarethumbs.com
127.0.0.1  img.rarethumbs.com
127.0.0.1  sexforguys.net
127.0.0.1  shemaleface.com
127.0.0.1  shyteenies.com
127.0.0.1  stockingsland.net
127.0.0.1  teensdot.org
127.0.0.1  teenstravel.net
127.0.0.1  tgpporn.net #[Javascript.Exploit]
127.0.0.1  www.tgpporn.net #[Google Warning]
127.0.0.1  tgps.biz
127.0.0.1  toonsman.net
127.0.0.1  xxvoyeur.net
# [Marketing Extensions Inc]
127.0.0.1  adshooter.com #[Adware.AdShooter][Wildcard DNS]
127.0.0.1  dl.adshooter.com
127.0.0.1  www.adshooter.com #[SpySweeper.Spy.Cookie]
127.0.0.1  affiliates.coolonlineoffers.com
127.0.0.1  dl.coolonlineoffers.com #[Trojan-Downloader.Win32.Small.hs]
127.0.0.1  www.coolonlineoffers.com
127.0.0.1  www.customersupporthelp.com
127.0.0.1  downloadrevenue.com
127.0.0.1  www.downloadrevenue.com
127.0.0.1  secure6.platinumbucks.com
127.0.0.1  www.platinumbucks.com
127.0.0.1  www.searchexpert.com
127.0.0.1  www.sexfind.com
127.0.0.1  searchforit.com #[eTrust.AdShooter.SearchForIt]
127.0.0.1  dl.searchforit.com #[SunBelt.SearchForIt.AdShooter]
127.0.0.1  www.searchforit.com #[Adware.Searchforit]
127.0.0.1  www.siteboxparking.com
127.0.0.1  surfenhance.com
127.0.0.1  dl.surfenhance.com
127.0.0.1  www.surfenhance.com
# [Milutin Milan]
127.0.0.1  www.1moms.net #[Malicious Links]
127.0.0.1  absolutethumbs.net
127.0.0.1  www.absolutethumbs.net
127.0.0.1  buttandass.net
127.0.0.1  www.buttandass.net
127.0.0.1  buttarchive.com
127.0.0.1  www.buttarchive.com
127.0.0.1  buttview.net
127.0.0.1  www.buttview.net
127.0.0.1  findmamas.com
127.0.0.1  www.findmamas.com
127.0.0.1  www.galsbox.com
127.0.0.1  www.gogoshemales.com
127.0.0.1  www.kuca-smrika.com
127.0.0.1  oldpleasure.com #[Google Warning]
127.0.0.1  www.oldpleasure.com #[Javascript.Exploit]
127.0.0.1  www.papasthumbs.com #[Google Warning]
127.0.0.1  www.penistested.com
127.0.0.1  www.*****-alarm.com #[Malicious Links]
127.0.0.1  www.sensualgals.com
127.0.0.1  www.system-killer.com
127.0.0.1  www.tetaane.com #[Google Warning]
127.0.0.1  thumbsarea.com
127.0.0.1  www.thumbsarea.com
127.0.0.1  www.yummygals.com
# [Monteg Inc]
127.0.0.1  www.thumbsearcher.net #[klikfeed.com]
127.0.0.1  www.toolbar4cash.com #[SunBelt.Toolbar4Cash]
# [Netdreams P/L]
127.0.0.1  www.escortsindex.com
127.0.0.1  www.internetpeace.com #[eTrust.Free Popup Killer]
# [Nikolay Zuyev]
127.0.0.1  agp-one.net #[Spamdexing]
127.0.0.1  akaokoichi.net #[Spamdexing]
127.0.0.1  grandsupport.net
127.0.0.1  www.iroveri.com
127.0.0.1  www.oldjim.com
# [Online Marketing Services]
127.0.0.1  www.statspage.net
127.0.0.1  trafficscripts.net
# [Pavel Egorov]
127.0.0.1  crackasd.info #[Spamdexing]
127.0.0.1  crackfgh.info
127.0.0.1  crackrty.info
127.0.0.1  serial2.crackrty.info #[Trojan-Downloader.Win32.Delf.bgy]
127.0.0.1  crackqwe.info
# [PayCounter.com, Inc]
127.0.0.1  paycounter.com #[Ad-Aware.Tracking.Cookie]
127.0.0.1  count.paycounter.com
127.0.0.1  images1.paycounter.com
127.0.0.1  in.paycounter.com #[SpySweeper.Spy.Cookie]
127.0.0.1  stats.paycounter.com
127.0.0.1  www.paycounter.com #[SunBelt.PayCounter.com]
127.0.0.1  sort.trafficjuicer.com
127.0.0.1  stats.trafficjuicer.com
127.0.0.1  www.trafficjuicer.com
# [Power Media Interactive]
127.0.0.1  www.ladylust.com
127.0.0.1  www.nudecash.com #[Google.Warning]
127.0.0.1  www.smut1000.com
# [PowerNetX, Inc][Trojan.PornDownloaderMCC]
127.0.0.1  www.18access.com
127.0.0.1  www.hentaidatabase.com
127.0.0.1  support.sextronix.com #[Wildcard DNS]
127.0.0.1  www.sextronix.com
# [Scott Willson]
127.0.0.1  1sexvideo.com #[Videoscash]
127.0.0.1  www.1sexvideo.com
127.0.0.1  69inch.com #[Videoscash]
127.0.0.1  www.69inch.com
# [Sergey Makarov]
127.0.0.1  getsearch.us
127.0.0.1  girlspark.net
127.0.0.1  111.girlspark.net
127.0.0.1  pornosuper.net
127.0.0.1  trax.pornosuper.net
127.0.0.1  teens.pornosuper.net #[IFrame.Exploit]
# [Soodkhet Kamchoom]
127.0.0.1  alllinx.info
127.0.0.1  cleanchain.net
127.0.0.1  dinet.info #[Trojan.Win32.Small.EV][Google Warning]
127.0.0.1  eqash.net
127.0.0.1  frdolls.net
127.0.0.1  frlynx.info
127.0.0.1  frsets.info
127.0.0.1  joutweb.net
127.0.0.1  linim.net #[eTrust.Win32/Secdrop.JU]
127.0.0.1  linkschain.net
127.0.0.1  linxlive.net
127.0.0.1  nwframe.net #[Win32/Nitwiz.A]
127.0.0.1  recdir.org
127.0.0.1  trflin.info #[Win32/TrojanDownloader.Ani.Gen]
127.0.0.1  zllin.info #[MHTMLRedir.Exploit][Win32/Dialer.KM]
# [Telemedia]
127.0.0.1  1stmovieclub.net #[Videoscash]
127.0.0.1  thumbs.1stmovieclub.net
127.0.0.1  www.1stmovieclub.net
127.0.0.1  onlybigmovies.com #[Videoscash]
127.0.0.1  www.onlybigmovies.com
# [Tim Parker]
127.0.0.1  www.myrealpics.com
127.0.0.1  www.picsdrive.com
127.0.0.1  www.picsplace.com
127.0.0.1  www.takebest.com #[klikfind.com][Trojan.TrustedZone]
127.0.0.1  www.zonebest.com #[MHTMLRedir.Exploit][SunBelt.zonebest.com]
# [Tribeca Productions]
127.0.0.1  adultid.us #[Win32/Cavitate]
127.0.0.1  www.adultid.us
127.0.0.1  www.tgp-megasite.com
127.0.0.1  www.netchicks.us
127.0.0.1  www.topsite.us
# [Unique Billing Systems Group]
127.0.0.1  mbsvalid1.com #[SecurityRisk.SexxPass]
127.0.0.1  mbsvalid2.com
127.0.0.1  membersmatter.net
127.0.0.1  www.membersmatter.net #[Trojan.Win32.Agent.afi]
127.0.0.1  auth.microbillsys.com #[sexxxpassport.com]
127.0.0.1  secure.microbillsys.com #[Symantec.MicroBillSys]
127.0.0.1  www.microbillsys.com #[Sophos.Micro Bill Systems]
127.0.0.1  mysexworld.com
127.0.0.1  www.mysexworld.com #[Malicious Links]
127.0.0.1  download.sexxxpassport.com #[Sophos.Micro Bill Systems][SunBelt.SexxxPassport]
127.0.0.1  www.sexxxpassport.com #[SecurityRisk.SexxPass][Trojan.Win32.Agent.afi]
# [Vasily Pupkin]
127.0.0.1  www.blonde-mature-hot-babes.biz #[Videoscash]
127.0.0.1  big-tits-orgasm.biz
127.0.0.1  www.big-tits-orgasm.biz #[Videoscash][dollarrevenue.com]
127.0.0.1  free-porn-thumbz.com
127.0.0.1  www.free-porn-thumbz.com #[Videoscash]
127.0.0.1  free-porn-galleries.biz
127.0.0.1  www.free-porn-galleries.biz
127.0.0.1  hairy-*****-hardcore-******.biz #[Videoscash]
127.0.0.1  www.hairy-*****-hardcore-******.biz
127.0.0.1  megapizda.com
127.0.0.1  www.megapizda.com #[Videoscash]
127.0.0.1  porn-forever.com
127.0.0.1  www.porn-forever.com
127.0.0.1  sex-list.us
127.0.0.1  www.sex-list.us
127.0.0.1  zhopa.net
127.0.0.1  www.zhopa.net
# [Vvisionlm dot]
127.0.0.1  www.hit4hit.com
127.0.0.1  www.hitboss.com #[CA.hitboss.com][SpySweeper.Spy.Cookie]
# [Waveflow Inc]
127.0.0.1  www.exitforcash.com
127.0.0.1  frontpagecash.com
127.0.0.1  www.frontpagecash.com
127.0.0.1  www.fpctraffic.com
127.0.0.1  fpctraffic2.com
127.0.0.1  www.fpctraffic2.com
# [Webbox media][Worex design]
127.0.0.1  boobs-in-hands.com #[IFrame.Exploit]
127.0.0.1  www.boobs-in-hands.com
127.0.0.1  boobsncocks.com #[IFrame.Exploit]
127.0.0.1  www.boobsncocks.com
127.0.0.1  fullhairybush.com #[IFrame.Exploit]
127.0.0.1  www.fullhairybush.com #[SiteAdvisor.fullhairybush.com]
127.0.0.1  hairypubis.com
127.0.0.1  www.hairypubis.com #[Javascript.Exploit]
127.0.0.1  jazzporno.com #[IFrame.Exploit]
127.0.0.1  www.jazzporno.com
127.0.0.1  voyeuradventures.net #[IFrame.Exploit]
127.0.0.1  www.voyeuradventures.net
# [Web Entertainment Group]
127.0.0.1  join4free.com
127.0.0.1  asians.join4free.com
127.0.0.1  clickthrough.wegcash.com
127.0.0.1  free.wegcash.com #[SunBelt.WegCash.com]
127.0.0.1  programs.wegcash.com #[Tenebril.wegcash.com]
127.0.0.1  promos.wegcash.com
# [Webpower Inc]
127.0.0.1  apps.clickcash.com
127.0.0.1  www.clickcash.com
127.0.0.1  cc.webpower.com
127.0.0.1  clickcash.webpower.com
127.0.0.1  orders.webpower.com #[SpySweeper.Spy.Cookie]
# [WmvMediaLease Group]
127.0.0.1  actionmpg.com
127.0.0.1  r.actionmpg.com
127.0.0.1  www.actionmpg.com
127.0.0.1  www2.actionmpg.com
127.0.0.1  activempg.com
127.0.0.1  www.activempg.com
127.0.0.1  www2.activempg.com
127.0.0.1  www.almostgayvideo.com
127.0.0.1  bestgayvideostream.com
127.0.0.1  boyslikemovies.com
127.0.0.1  boysloveyou.com
127.0.0.1  www.boysloveyou.com
127.0.0.1  champmovie.com
127.0.0.1  www2.champmovie.com
127.0.0.1  clickmpg.com
127.0.0.1  www.clickmpg.com
127.0.0.1  www2.clickmpg.com
127.0.0.1  cosmomovie.com
127.0.0.1  www.cosmomovie.com
127.0.0.1  www2.cosmomovie.com
127.0.0.1  crazycinema.net
127.0.0.1  www.crazycinema.net
127.0.0.1  www2.crazycinema.net
127.0.0.1  hellompgs.com
127.0.0.1  fhg.hellompgs.com
127.0.0.1  www.hellompgs.com
127.0.0.1  www2.hellompgs.com
127.0.0.1  hqmovieclub.com
127.0.0.1  www.hqmovieclub.com
127.0.0.1  www2.hqmovieclub.com
127.0.0.1  lovethevideo.com
127.0.0.1  www.lovethevideo.com
127.0.0.1  www2.lovethevideo.com
127.0.0.1  megasexonvideo.com
127.0.0.1  www.megasexonvideo.com
127.0.0.1  www2.megasexonvideo.com
127.0.0.1  movie-rise.com
127.0.0.1  www.movie-rise.com
127.0.0.1  www2.movie-rise.com
127.0.0.1  moviestarsonvideo.com
127.0.0.1  www.moviestarsonvideo.com
127.0.0.1  mpgbank.com
127.0.0.1  www2.mpgbank.com
127.0.0.1  mpgbox.com
127.0.0.1  www.mpgbox.com
127.0.0.1  www2.mpgbox.com
127.0.0.1  mpgdot.com
127.0.0.1  www2.mpgdot.com
127.0.0.1  onlinegaymoviestore.com
127.0.0.1  onlinegayvideostore.com
127.0.0.1  www.realtimegay.com
127.0.0.1  redhatmovie.com
127.0.0.1  www.redhatmovie.com
127.0.0.1  www2.redhatmovie.com
127.0.0.1  sexmoviesisland.com
127.0.0.1  videosexygirls.net
127.0.0.1  www2.videosexygirls.net
127.0.0.1  wmvmedialease.com #[Trojan.Win32.Agent.ahp]
127.0.0.1  worldmoviegay.com
# [XCell Inc]
127.0.0.1  www.emporn.com #[Malicious.Links.Zango]
127.0.0.1  servedby.fathomtech.com
127.0.0.1  www.freeblowjobmovies.us #[Malicious.Links.Zango]
127.0.0.1  www.freeblowjobvideos.us
127.0.0.1  www.mommaporn.com
127.0.0.1  www.pokemonporn.us #[Malicious.Links.Zango]
127.0.0.1  www.wwe-divas.org
127.0.0.1  servedby.xcelltech.com
127.0.0.1  www.xcelltech.com

# [XSC Incorporated]
127.0.0.1  smutvidoftheday.com #[Win32/TrojanDownloader.Agent.NJC]
127.0.0.1  www.smutvidoftheday.com #[SiteAdvisor.smutvidoftheday.com]
127.0.0.1  www.xscincorporated.com
#end of lines added by WinHelp2002


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Roaster on 2007-08-26
Ridiculous!!

---

### Post by vdawg on 2007-08-26
lol, well maybe thats the problem

here's my hosts file

vic@puter:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 puter

thats it - everything worken fine fer me... 

ps: if you use firefox you can use adblock to block unwanted sites - doing it at the hosts level is probably chewing up your cpu time but that doesnt explain why you get directed to weird sites...

---

### Post by Pablopcv on 2007-08-27
tnx a lot vdawg. the problem its solved... Adblock its working fine. It was a good suggestion, thanks again!

<EDIT>
It seemed like that but now it showed up again

---

### Post by xc3RnbFO8P on 2007-08-27
Here is mine.

127.0.0.1 localhost
127.0.1.1 rig-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Dark Star on 2007-08-27
Some 1 wrap the text in code :)

---

### Post by tgalati4 on 2007-08-27
Does this look like the first modern virus for Linux?

---

### Post by Dark Star on 2007-08-27
:lol: Yeah a trojan in Linux :(

---

### Post by Pinger05 on 2007-08-27
Is your Ubuntu computer a DNS server?  I dont know why but it seems to me that your hosts file is way too big.  But then again I am no professional Linux admin.

<EDIT>
err nevermind, the rest of the posts finally loaded.

---

### Post by Pablopcv on 2007-08-27
oh sorry about that. I didn't realized that it was that big. 

The problem showed up again hahah I cant believe it... I installed No-Script too but the problem is that neither adblock or noscript detect the real source of the page...

Yes, its kind of a rare malware problem in Ubuntu... I think that Viruses and malware will increase if ubuntu keeps gaining popularity.

---

### Post by bodhi.zazen on 2007-08-27
Nice to see a link to that hosts file :)

That thread is a little old, so I added some information.

FYI you need to install tofrodos then run the script ...

```
sudo apt-get install tofrodos
```

You may also want to look at privoxy (you can run proviox with or without tor)

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)
	[http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html](http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html)

privoxy (without tor) will add some additional ad blocking (although I still like the hosts file the most)

---

### Post by upthelum on 2007-08-27
At a glance there's something way wrong with your hosts file. The previous hosts files posted by others i think are a typical example and mine's is the same, no more than 10 lines or so. I haven't read all the file yet so wil have a browse it looks quite BIG...

---

### Post by upthelum on 2007-08-27
> **Dark Star said:**
> :lol: Yeah a trojan in Linux :(

Hey how did Pablopcv manage to get a hosts file like that?

---

### Post by mrt on 2007-08-27
> **upthelum said:**
> Hey how did Pablopcv manage to get a hosts file like that?


[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

Read all about it; it's an effective way to block LOTS of internet crap.

---

### Post by bodhi.zazen on 2007-08-27
> **mrt said:**
> [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

Read all about it; it's an effective way to block LOTS of internet crap.

Well, IMO, another nice feature of using a hosts file is that it protects more then just Firefox ...

---

### Post by Pablopcv on 2007-08-27
yes, my host its that big cuz I pasted a large list of unwanted website on in...

New weird things appeared... I cant login with gaim or amsn and the Firefox default search bar redirects me to [www.searchnut.com](www.searchnut.com) (that its blocked by my host configuration) instead google...

I found this suspicious script direction:

       > ---->http://adserving.cpxinteractive.com/imp?z=0&Z=0x0&s=119225&y=28<----

be careful with that, it can be the cause of my problem

---

### Post by wirelessmonkey on 2007-08-28
> **Pablopcv said:**
> yes, my host its that big cuz I pasted a large list of unwanted website on in...

New weird things appeared... I cant login with gaim or amsn and the Firefox default search bar redirects me to [www.searchnut.com](www.searchnut.com) (that its blocked by my host configuration) instead google...

I found this suspicious script direction:

       

be careful with that, it can be the cause of my problem

Did I understand that correctly? You purposefully added those to your /etc/hosts file?

Well, there's 'a' source of your problems... each of those sites is now resolving to your machine, so far as your system is concerned

---

### Post by wirelessmonkey on 2007-08-28
As an aside, your hosts list looks similar to someting that happened to a novice metaploit-framework user, if my memory serves me.  Have you been playing with any utilities? What generated that list for you, or did you do it yourseslf?

---

### Post by nowshining on 2007-08-28
Actually I have a 344 thousand Plus hosts file and all works fine for me - my computer is quick and it's about 10 mb plus - so I won't post mine, lolz.. :P I host my own hosts file for others - but since I switched to ubuntu I gotta get hostsman to work with it as i do not want dups so I am only updating it by hand right now, i add others together, ;) anyway back to the post Everything works fine for me by the way... and I am using the regular build of firefox from mozilla - the one incl. with ubuntu sucks really bad.. with NO EXTENSIONS except default...and gong direct right now - i have proxomitron and have changed the google cookie to all zeroes with it, removed some forum cookies tracking me around the forum, etc... but right now I am direct - lolz... ;)

---

### Post by Pablopcv on 2007-08-28
> **wirelessmonkey said:**
> As an aside, your hosts list looks similar to someting that happened to a novice metaploit-framework user, if my memory serves me.  Have you been playing with any utilities? What generated that list for you, or did you do it yourseslf?

I generated it using this trend info [http://ubuntuforums.org/showthread.php?t=241460](http://ubuntuforums.org/showthread.php?t=241460)

---

### Post by por100pre1 on 2007-08-28
> **Pablopcv said:**
> hi. I'm having an adware issue what its very uncommon since i'm using ubuntu edgy. When I try to enter to any site (eg: google, yahoo, whatever) i'm redirected to a page with adds and no real info in the page source or in the page information. I tracked the source and its from this guys adserving.cpxinteractive.com.

I googled it and its seems like some windows users have this problem too and they fix it running something to remove it... but I have no clue how to get rid of this in ubuntu. I tried removing private info, blocking the site editing hosts and hosts.deny and connecting to a different isp but didnt work.

Im using:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20070601 Firefox/2.0.0.4 (Swiftfox) 
Ubuntu 6.10 edgy 


thanks
pcv

Does this happen with other browsers or just Swiftfox? Maybe the browser is poisoned with an evil extension or plugin. To check by running the browser in safe mode can be useful.

```
firefox -safe-mode
```

or:

```
swiftfox -safe-mode
```
.
You may need to disable whatever host fix you already have. :-k

---

### Post by Pablopcv on 2007-08-28
> **por100pre1 said:**
> Does this happen with other browsers or just Swiftfox? Maybe the browser is poisoned with an evil extension or plugin. To check by running the browser in safe mode can be useful.

```
firefox -safe-mode
```

or:

```
swiftfox -safe-mode
```
.
You may need to disable whatever host fix you already have. :-k

the ad page has not appeared in safe mode so far.

yeah, I already restored to my original hosts file. Thank you.

---

### Post by weblordpepe on 2007-08-28
It would be like a kernel level thing if all the apps are being silly.

---

### Post by por100pre1 on 2007-08-28
> **Pablopcv said:**
> the ad page has not appeared in safe mode so far.

yeah, I already restored to my original hosts file. Thank you.

It would be good to review your extensions and plugins, especially your extensions. One of them can be causing this. :)

---

### Post by Pablopcv on 2007-08-28
yes, thanks all four your help and attention.

the ad finally showed up in safe mode too, it took longer but after all there is...

I will keep testing stuff to find the cause of this annoying ad page.

thanks again for your help

---

### Post by weblordpepe on 2007-08-29
Try using things that aren't browsers. Can you traceroute to the web page? 
What about using wget?

Try accessing the page with wget. Even if you just download the index.html of the web page it would let you know if you're dealing with apps or network routing.
EDIT: Or even lynx, the text based browser.

---

### Post by Pablopcv on 2007-08-29
> **weblordpepe said:**
> Try using things that aren't browsers. Can you traceroute to the web page? 
What about using wget?

Try accessing the page with wget. Even if you just download the index.html of the web page it would let you know if you're dealing with apps or network routing.
EDIT: Or even lynx, the text based browser.


oh good idea, lets see... It gets the page with wget but with lynx it get this

```
400 Bad Request

   Google  
            Error

                                  Bad Request

     Your client has issued a malformed or illegal request.

```

:-k

---

### Post by Pablopcv on 2007-08-29
I tried again with a different page and wget and this thime it gave me the source code of the ad page :confused:

wget worked when I tried at first with google but I not this time... Its very confusig
lynx was the same...

---

### Post by weblordpepe on 2007-08-30
smells like a rootkit or something. I wonder if you are using one of those ISPs that are putting advertising into web pages.

---

### Post by por100pre1 on 2007-08-30
> **weblordpepe said:**
> smells like a rootkit or something. I wonder if you are using one of those ISPs that are putting advertising into web pages.

:shock: It could be a rootkit. It would be good to do some rootkit scanning...

Pablopcv, try installing chkrootkit and rkhunter:

```
sudo aptitude install chkrootkit rkhunter
```

and run them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by Pablopcv on 2007-08-30
> **weblordpepe said:**
> smells like a rootkit or something. I wonder if you are using one of those ISPs that are putting advertising into web pages.

I dont think so. I have 2 different ISPs with 2 different routers and the problem shows up anyway.

> Pablopcv, try installing chkrootkit and rkhunter:

mmm...Nothing suspicious, only found this:

 ```
Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory) 
```

dont know if its normal... Is the first time that I use rkhunter

here is the complete log:

```
ROOTDIR is `/'
Checking `amd'... not found
Checking `basename'... not infected
Checking `biff'... not found
Checking `chfn'... not infected
Checking `chsh'... not infected
Checking `cron'... not infected
Checking `date'... not infected
Checking `du'... not infected
Checking `dirname'... not infected
Checking `echo'... not infected
Checking `egrep'... not infected
Checking `env'... not infected
Checking `find'... not infected
Checking `fingerd'... not found
Checking `gpm'... not found
Checking `grep'... not infected
Checking `hdparm'... not infected
Checking `su'... not infected
Checking `ifconfig'... not infected
Checking `inetd'... not infected
Checking `inetdconf'... not found
Checking `identd'... not found
Checking `init'... not infected
Checking `killall'... not infected
Checking `ldsopreload'... not infected
Checking `login'... not infected
Checking `ls'... not infected
Checking `lsof'... not infected
Checking `mail'... not found
Checking `mingetty'... not found
Checking `netstat'... not infected
Checking `named'... not found
Checking `passwd'... not infected
Checking `pidof'... not infected
Checking `pop2'... not found
Checking `pop3'... not found
Checking `ps'... not infected
Checking `pstree'... not infected
Checking `rpcinfo'... not infected
Checking `rlogind'... not found
Checking `rshd'... not found
Checking `slogin'... not infected
Checking `sendmail'... not infected
Checking `sshd'... not found
Checking `syslogd'... not infected
Checking `tar'... not infected
Checking `tcpd'... not infected
Checking `tcpdump'... not infected
Checking `top'... not infected
Checking `telnetd'... not found
Checking `timed'... not found
Checking `traceroute'... not found
Checking `vdir'... not infected
Checking `w'... not infected
Checking `write'... not infected
Checking `aliens'... no suspect files
Searching for sniffer's logs, it may take a while... nothing found
Searching for HiDrootkit's default dir... nothing found
Searching for t0rn's default files and dirs... nothing found
Searching for t0rn's v8 defaults... nothing found
Searching for Lion Worm default files and dirs... nothing found
Searching for RSHA's default files and dir... nothing found
Searching for RH-Sharpe's default files... nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/usr/lib/jvm/java-6-sun-1.6.0.00/.systemPrefs
/usr/lib/jvm/.java-6-sun.jinfo
/lib/modules/2.6.17-12-generic/volatile/.mounted

Searching for LPD Worm files and dirs... nothing found
Searching for Ramen Worm files and dirs... nothing found
Searching for Maniac files and dirs... nothing found
Searching for RK17 files and dirs... nothing found
Searching for Ducoci rootkit... nothing found
Searching for Adore Worm... nothing found
Searching for ShitC Worm... nothing found
Searching for Omega Worm... nothing found
Searching for Sadmind/IIS Worm... nothing found
Searching for MonKit... nothing found
Searching for Showtee... nothing found
Searching for OpticKit... nothing found
Searching for T.R.K... nothing found
Searching for Mithra... nothing found
Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
Searching for Volc rootkit... nothing found
Searching for Gold2 rootkit... nothing found
Searching for TC2 Worm default files and dirs... nothing found
Searching for Anonoying rootkit default files and dirs... nothing found
Searching for ZK rootkit default files and dirs... nothing found
Searching for ShKit rootkit default files and dirs... nothing found
Searching for AjaKit rootkit default files and dirs... nothing found
Searching for zaRwT rootkit default files and dirs... nothing found
Searching for Madalin rootkit default files... nothing found
Searching for Fu rootkit default files... nothing found
Searching for ESRK rootkit default files... nothing found
Searching for rootedoor... nothing found
Searching for anomalies in shell history files... nothing found
Checking `asp'... not infected
Checking `bindshell'... not infected
Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[4674], /sbin/dhclient3[4704])
Checking `w55808'... not infected
Checking `wted'... chkwtmp: nothing deleted
Checking `scalper'... not infected
Checking `slapper'... not infected
Checking `z2'... chklastlog: nothing deleted
pcv@pcv-laptop:~$ sudo rkhunter --update && sudo rkhunter -c -sk
Running updater...

Mirrorfile /var/lib/rkhunter/db/mirrors.dat rotated
Using mirror http://www.rootkit.nl/rkhunter
[DB] Mirror file                      :  
Update available
/var/lib/rkhunter/db/mirrors.dat
  Action: Database updated (current version: 2005050700, new version 2006092302)
[DB] MD5 hashes system binaries       : Update available
  Action: Database updated (current version: 2006021400, new version 2006022800)
[DB] Operating System information     : Update available
  Action: Database updated (current version: 2005102800, new version 2006093000)
[DB] MD5 blacklisted tools/binaries   : Up to date
[DB] Known good program versions      : Update available
  Action: Database updated (current version: 2006021400, new version 2006031400)
[DB] Known bad program versions       : Update available
  Action: Database updated (current version: 2006021400, new version 2006031400)




Ready.


Rootkit Hunter 1.2.8 is running

Determining OS... Ready


Checking binaries
* Selftests
     Strings (command)-e                                         [ OK ]


* System tools
  Performing 'known bad' check...
   /bin/cat-e                                                    [ OK ]
   /bin/chmod-e                                                  [ OK ]
   /bin/chown-e                                                  [ OK ]
   /bin/date-e                                                   [ OK ]
   /bin/df-e                                                     [ OK ]
   /bin/dmesg-e                                                  [ OK ]
   /bin/echo-e                                                   [ OK ]
   /bin/ed-e                                                     [ OK ]
   /bin/egrep-e                                                  [ OK ]
   /bin/fgrep-e                                                  [ OK ]
   /bin/grep-e                                                   [ OK ]
   /bin/kill-e                                                   [ OK ]
   /bin/login-e                                                  [ OK ]
   /bin/ls-e                                                     [ OK ]
   /bin/more-e                                                   [ OK ]
   /bin/mount-e                                                  [ OK ]
   /bin/netstat-e                                                [ OK ]
   /bin/ps-e                                                     [ OK ]
   /bin/sh-e                                                     [ OK ]
   /bin/su-e                                                     [ OK ]
   /sbin/depmod-e                                                [ OK ]
   /sbin/ifconfig-e                                              [ OK ]
   /sbin/ifdown-e                                                [ OK ]
   /sbin/ifup-e                                                  [ OK ]
   /sbin/init-e                                                  [ OK ]
   /sbin/insmod-e                                                [ OK ]
   /sbin/ip-e                                                    [ OK ]
   /sbin/lsmod-e                                                 [ OK ]
   /sbin/modinfo-e                                               [ OK ]
   /sbin/modprobe-e                                              [ OK ]
   /sbin/rmmod-e                                                 [ OK ]
   /sbin/runlevel-e                                              [ OK ]
   /sbin/sulogin-e                                               [ OK ]
   /sbin/sysctl-e                                                [ OK ]
   /sbin/syslogd-e                                               [ OK ]
   /usr/bin/basename-e                                           [ OK ]
   /usr/bin/chattr-e                                             [ OK ]
   /usr/bin/du-e                                                 [ OK ]
   /usr/bin/file-e                                               [ OK ]
   /usr/bin/find-e                                               [ OK ]
   /usr/bin/groups-e                                             [ OK ]
   /usr/bin/head-e                                               [ OK ]
   /usr/bin/killall-e                                            [ OK ]
   /usr/bin/last-e                                               [ OK ]
   /usr/bin/lastlog-e                                            [ OK ]
   /usr/bin/less-e                                               [ OK ]
   /usr/bin/locate-e                                             [ OK ]
   /usr/bin/logger-e                                             [ OK ]
   /usr/bin/lsattr-e                                             [ OK ]
   /usr/bin/md5sum-e                                             [ OK ]
   /usr/bin/passwd-e                                             [ OK ]
   /usr/bin/pstree-e                                             [ OK ]
   /usr/bin/sha1sum-e                                            [ OK ]
   /usr/bin/size-e                                               [ OK ]
   /usr/bin/slocate-e                                            [ OK ]
   /usr/bin/sort-e                                               [ OK ]
   /usr/bin/stat-e                                               [ OK ]
   /usr/bin/strace-e                                             [ OK ]
   /usr/bin/strings-e                                            [ OK ]
   /usr/bin/test-e                                               [ OK ]
   /usr/bin/top-e                                                [ OK ]
   /usr/bin/touch-e                                              [ OK ]
   /usr/bin/users-e                                              [ OK ]
   /usr/bin/vmstat-e                                             [ OK ]
   /usr/bin/w-e                                                  [ OK ]
   /usr/bin/watch-e                                              [ OK ]
   /usr/bin/wc-e                                                 [ OK ]
   /usr/bin/wget-e                                               [ OK ]
   /usr/bin/whatis-e                                             [ OK ]
   /usr/bin/whereis-e                                            [ OK ]
   /usr/bin/which-e                                              [ OK ]
   /usr/bin/who-e                                                [ OK ]
   /usr/bin/whoami-e                                             [ OK ]
   /usr/sbin/adduser-e                                           [ OK ]
   /usr/sbin/chroot-e                                            [ OK ]
   /usr/sbin/cron-e                                              [ OK ]
   /usr/sbin/tcpd-e                                              [ OK ]
   /usr/sbin/useradd-e                                           [ OK ]
   /usr/sbin/usermod-e                                           [ OK ]
   /usr/sbin/vipw-e                                              [ OK ]
  Performing 'known good' check...


Check rootkits
* Default files and directories
   Rootkit '55808 Trojan - Variant A'... -e                      [ OK ]
   ADM Worm... -e                                                [ OK ]
   Rootkit 'AjaKit'... -e                                        [ OK ]
   Rootkit 'aPa Kit'... -e                                       [ OK ]
   Rootkit 'Apache Worm'... -e                                   [ OK ]
   Rootkit 'Ambient (ark) Rootkit'... -e                         [ OK ]
   Rootkit 'Balaur Rootkit'... -e                                [ OK ]
   Rootkit 'BeastKit'... -e                                      [ OK ]
   Rootkit 'beX2'... -e                                          [ OK ]
   Rootkit 'BOBKit'... -e                                        [ OK ]
   Rootkit 'CiNIK Worm (Slapper.B variant)'... -e                [ OK ]
   Rootkit 'Danny-Boy's Abuse Kit'... -e                         [ OK ]
   Rootkit 'Devil RootKit'... -e                                 [ OK ]
   Rootkit 'Dica'... -e                                          [ OK ]
   Rootkit 'Dreams Rootkit'... -e                                [ OK ]
   Rootkit 'Duarawkz'... -e                                      [ OK ]
   Rootkit 'Flea Linux Rootkit'... -e                            [ OK ]
   Rootkit 'FreeBSD Rootkit'... -e                               [ OK ]
   Rootkit '****`it Rootkit'... -e                               [ OK ]
   Rootkit 'GasKit'... -e                                        [ OK ]
   Rootkit 'Heroin LKM'... -e                                    [ OK ]
   Rootkit 'HjC Kit'... -e                                       [ OK ]
   Rootkit 'ignoKit'... -e                                       [ OK ]
   Rootkit 'ImperalsS-FBRK'... -e                                [ OK ]
   Rootkit 'Irix Rootkit'... -e                                  [ OK ]
   Rootkit 'Kitko'... -e                                         [ OK ]
   Rootkit 'Knark'... -e                                         [ OK ]
   Rootkit 'Li0n Worm'... -e                                     [ OK ]
   Rootkit 'Lockit / LJK2'... -e                                 [ OK ]
   Rootkit 'MRK'... -e                                           [ OK ]
   Rootkit 'Ni0 Rootkit'... -e                                   [ OK ]
   Rootkit 'RootKit for SunOS / NSDAP'... -e                     [ OK ]
   Rootkit 'Optic Kit (Tux)'... -e                               [ OK ]
   Rootkit 'Oz Rootkit'... -e                                    [ OK ]
   Rootkit 'Portacelo'... -e                                     [ OK ]
   Rootkit 'R3dstorm Toolkit'... -e                              [ OK ]
   Rootkit 'RH-Sharpe's rootkit'... -e                           [ OK ]
   Rootkit 'RSHA's rootkit'... -e                                [ OK ]
   Sebek LKM-e                                                   [ OK ]
   Rootkit 'Scalper Worm'... -e                                  [ OK ]
   Rootkit 'Shutdown'... -e                                      [ OK ]
   Rootkit 'SHV4'... -e                                          [ OK ]
   Rootkit 'SHV5'... -e                                          [ OK ]
   Rootkit 'Sin Rootkit'... -e                                   [ OK ]
   Rootkit 'Slapper'... -e                                       [ OK ]
   Rootkit 'Sneakin Rootkit'... -e                               [ OK ]
   Rootkit 'Suckit Rootkit'... -e                                [ OK ]
   Rootkit 'SunOS Rootkit'... -e                                 [ OK ]
   Rootkit 'Superkit'... -e                                      [ OK ]
   Rootkit 'TBD (Telnet BackDoor)'... -e                         [ OK ]
   Rootkit 'TeLeKiT'... -e                                       [ OK ]
   Rootkit 'T0rn Rootkit'... -e                                  [ OK ]
   Rootkit 'Trojanit Kit'... -e                                  [ OK ]
   Rootkit 'Tuxtendo'... -e                                      [ OK ]
   Rootkit 'URK'... -e                                           [ OK ]
   Rootkit 'VcKit'... -e                                         [ OK ]
   Rootkit 'Volc Rootkit'... -e                                  [ OK ]
   Rootkit 'X-Org SunOS Rootkit'... -e                           [ OK ]
   Rootkit 'zaRwT.KiT Rootkit'... -e                             [ OK ]

* Suspicious files and malware
   Scanning for known rootkit strings-e                          [ OK ]
   Scanning for known rootkit files-e                            [ OK ]
   Testing running processes... -e                               [ OK ]
   Miscellaneous Login backdoors-e                               [ OK ]
   Miscellaneous directories-e                                   [ OK ]
   Software related files-e                                      [ OK ]
   Sniffer logs-e                                                [ OK ]

* Trojan specific characteristics
   shv4
     Checking /etc/rc.d/rc.sysinit-e                             [ Not found ]
     Checking /etc/inetd.conf-e                                  [ Not found ]
     Checking /etc/xinetd.conf-e                                 [ Skipped ]

* Suspicious file properties
   chmod properties
     Checking /bin/ps-e                                          [ Clean ]
     Checking /bin/ls-e                                          [ Clean ]
     Checking /usr/bin/w-e                                       [ Clean ]
     Checking /usr/bin/who-e                                     [ Clean ]
     Checking /bin/netstat-e                                     [ Clean ]
     Checking /bin/login-e                                       [ Clean ]
   Script replacements
     Checking /bin/ps-e                                          [ Clean ]
     Checking /bin/ls-e                                          [ Clean ]
     Checking /usr/bin/w-e                                       [ Clean ]
     Checking /usr/bin/who-e                                     [ Clean ]
     Checking /bin/netstat-e                                     [ Clean ]
     Checking /bin/login-e                                       [ Clean ]

* OS dependant tests

   Linux
     Checking loaded kernel modules... -e                        [ OK ]
     Checking files attributes-e                                 [ OK ]
     Checking LKM module path-e                                  [ OK ]


Networking
* Check: frequently used backdoors
  Port 2001: Scalper Rootkit-e                                   [ OK ]
  Port 2006: CB Rootkit-e                                        [ OK ]
  Port 2128: MRK-e                                               [ OK ]
  Port 14856: Optic Kit (Tux)-e                                  [ OK ]
  Port 47107: T0rn Rootkit-e                                     [ OK ]
  Port 60922: zaRwT.KiT-e                                        [ OK ]

* Interfaces
     Scanning for promiscuous interfaces-e                       [ OK ]


System checks
* Allround tests
   Checking hostname... Found. Hostname is pcv-laptop
   Checking for passwordless user accounts... OK
   Checking for differences in user accounts... -e                       [ NA ]
   Checking for differences in user groups... Creating file It seems this is your first time.
   Checking boot.local/rc.local file... 
     - /etc/rc.local-e                                           [ OK ]
     - /etc/rc.d/rc.local-e                                      [ Not found ]
     - /usr/local/etc/rc.local-e                                 [ Not found ]
     - /usr/local/etc/rc.d/rc.local-e                            [ Not found ]
     - /etc/conf.d/local.start-e                                 [ Not found ]
     - /etc/init.d/boot.local-e                                  [ Not found ]
   Checking rc.d files... -e                                     [ Not found ]
   Checking history files
     Bourne Shell-e                                              [ Not Found ]

* Filesystem checks
   Checking /dev for suspicious files... -e                      [ OK ]
   Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory) 


Application advisories
* Application scan
   Checking Apache2 modules ... -e                               [ Not found ]
   Checking Apache configuration ... -e                          [ OK ]

* Application version scan
   - Exim MTA 4.62 -e                                            [ Unknown ]
   - GnuPG 1.4.3 -e                                              [ Unknown ]
   - OpenSSL 0.9.8b -e                                           [ Unknown ]

Your system contains some unknown version numbers. Please run Rootkit Hunter
with the --update parameter or fill in the contact form (www.rootkit.nl)


Security advisories
* Check: Groups and Accounts
   Searching for /etc/passwd... -e                               [ Found ]
   Checking users with UID '0' (root)... -e                      [ OK ]

* Check: SSH
   Searching for sshd_config... 

* Check: Events and Logging
   Search for syslog configuration... -e                         [ OK ]
   Checking for running syslog slave... -e                       [ OK ]
   Checking for logging to remote system... -e                   [ OK (no remote logging) ]


---------------------------- Scan results ----------------------------

MD5
MD5 compared: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 35 seconds

```

---

### Post by Mud.Knee.Havoc on 2007-08-30
> **wirelessmonkey said:**
> Did I understand that correctly? You purposefully added those to your /etc/hosts file?

Well, there's 'a' source of your problems... each of those sites is now resolving to your machine, so far as your system is concerned

There's nothing wrong with his hosts file.  It's a method to BLOCK harmful websites.

---

### Post by dasunst3r on 2007-08-30
It's probably one of those malicious extensions.  Try issuing this command in the terminal: *mv .mozilla .mozilla-old* and relaunching Firefox.  This is going make you a new user profile for Firefox or Swiftfox.

---

### Post by weblordpepe on 2007-09-01
Yea thats right. Do that. At least that'll reset all the user-specific configuration.

---

### Post by motin on 2007-09-04
I don't have a solution but am nevertheless interested in this subject. 

Everybody that is replying please:
 - Stop complaining on the hosts-file - he has restored it to normal and it should have been fine before that as well.
 - Stop suggesting Firefox-specific solutions - it is pretty evident that his whole system is affected.

I just _have_ to ask: Does the problem go away after you've run
```
killall wineserver
```
?

Also, it would be great if you could fire up say VMWare of VirtualBox and connect from there. If you are still getting that redirect you be almost certain that your connections is hijacked in some way and not your Ubuntu machine. Another way to try this would be to try with someone's laptop from your connection.

---

### Post by jso2897 on 2007-09-04
I don't know if this will help at all, but Lavasoft now offers a free version of Ad-Aware for linux.

---

### Post by crjackson on 2007-09-04
Wow, this IS a disturbing therad.  My MAIN reason for moving to ubuntu is security and lack of virus problems.

I hope this isn't the shape of things to come.  **Thread=Subscribed**!

---

### Post by phocis850 on 2007-09-04
There are many Virus's out there for Linux.
You need to understand that Linux runs over half the servers that run the internet, and is vulnerable to attack at any minute.  The way Linux is built is more secure than the Windows framework.

---

### Post by SOULRiDER on 2007-09-04
> **crjackson said:**
> Wow, this IS a disturbing therad.  My MAIN reason for moving to ubuntu is security and lack of virus problems.

I hope this isn't the shape of things to come.  **Thread=Subscribed**!

While there are viruses, the number is very very samll and linux is tight. Its more probable that you get hit by a meteor than to get one one those :P

---

### Post by crjackson on 2007-09-05
> **jso2897 said:**
> I don't know if this will help at all, but Lavasoft now offers a free version of Ad-Aware for linux.

Really?  I can't find it.  Can you give me a link?

---

### Post by bodhi.zazen on 2007-09-05
> **crjackson said:**
> Wow, this IS a disturbing therad.  My MAIN reason for moving to ubuntu is security and lack of virus problems.

I hope this isn't the shape of things to come.  **Thread=Subscribed**!

> **jso2897 said:**
> I don't know if this will help at all, but Lavasoft now offers a free version of Ad-Aware for linux.

> **phocis850 said:**
> There are many Virus's out there for Linux.
You need to understand that Linux runs over half the servers that run the internet, and is vulnerable to attack at any minute.  The way Linux is built is more secure than the Windows framework.

OK, just a word to address FUD that always drifts into these kinds of threads ...

First Adware ... I have been running Linux for years now and have never seen the kinds of issues that are rampant on other OS.

The two biggest potential gaps are, IMO, java and cookies.

For java, install NoScript and block all. Add your routine, trusted sites to the white list ...

For cookies, same, deny all and add your trusted sites to the white list.

====

With that said, I would be very interested to see the results of Lavasoft, Linux version.

I am not saying such things *never* happen, just that they are quite rare.

====

And about those viruses ... first there are no let us say active Linux viruses at the moment. Viruses take advantage of holes in the code, so when a Linux virus is "released" the hole in the code is patched fairly rapidly.

The security vulnerabilities in Linux are different.

See this link for info : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by l0co on 2007-09-10
Returning to the problem - I had the same issue (searchportal) but only for opera. Removal of ~/.opera helped, so I think it was opera-specific malicious extension. The other browsers were OK, even those in my VirtualBox WinXP.

But there's interesting thing, that my lynx cannot get the google.com properly, because Google returns HTTP 400 Bad Request. I don't know whether is a problem of my lynx settings, version, or something else. My lynx is:

[INDENT]Lynx Version 2.8.5rel.1 (04 Feb 2004)
libwww-FM 2.14, SSL-MM 1.4.1, GNUTLS 1.2.9
Built on linux-gnu Mar  2 2006 16:43:09[/INDENT]

And now I'm thinking whether I have any trojan/viruses on my OS or it was just the opera problem and my system is OK. So, can your lynx-s access google.com properly?

---

### Post by sdowney717 on 2007-09-10
[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

would it be a good idea to use this as a hosts file?

---

### Post by bodhi.zazen on 2007-09-10
> **sdowney717 said:**
> [http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

would it be a good idea to use this as a hosts file?

Yes. There is a script to install it posted here :

[http://ubuntuforums.org/showpost.php?p=1505364&postcount=2](http://ubuntuforums.org/showpost.php?p=1505364&postcount=2)

---

### Post by Rhubarb on 2007-09-10
To try to isolate where the problem is, I recommend you try the ubuntu live CD, and check to see if the ads popup.
(from your hard drive - installed ubuntu partition) Try to create a restricted account, and check for ads in that new (testing) account.

---

### Post by cleverselfreferentialname on 2007-09-14
It can still be a network problem and not be the ISP or the router. It could be someone else on the network messing with you, especially if you're utilizing wifi.

I have used linux for about three years now and I have NEVER seen any adware or spyware. I seriously doubt that's the case.

Note that it's more clean to do:

0.0.0.0 hostiwanttoblock.tld

in your hosts file. That causes an immediate timeout when you try to connect to one of those hosts. Uses fewer clock cycles.

EDIT: Yeah, I know, timeout isn't a great word for it.

---

### Post by g2g591 on 2007-09-14
u try resetting your router to factory settings if the ads pop up on a live-cd, like someone said, someone could have changed settings on you.

---

### Post by mali2297 on 2007-10-16
> **Pablopcv said:**
> yes, thanks all four your help and attention.

the ad finally showed up in safe mode too, it took longer but after all there is...

I will keep testing stuff to find the cause of this annoying ad page.

thanks again for your help

It would be interesting to know if you were able to find the cause of this unusual problem.
:popcorn:

---

### Post by Wiebelhaus on 2007-10-16
Show me this "Ad-aware for linux" It's not listed at lavasoft.com , betanews.com , filehippo.com , download.com or google searches.


It's most obviously a browser / temp files issue , remove these and reinstall your browser , this is the reason Gnu/linux is modular , you can completely gut any program and reinstall when it's acting funny or you damaged it.

---

### Post by hhhobbit on 2007-10-17
It may help you that you will need a pseudo-web server and perhaps a PAC (Proxy Auto Configuration) file that will help you but PLEASE do not post the hosts file in the forum.  No HJT logs here please.  Here is what I have for you (MVPS is associated with Windows and IE primarily)

[http://www.securemecca.com](http://www.securemecca.com)
(sister site)
[http://www.hostsfile.org](http://www.hostsfile.org)

What it sounds like, since you say it has the same behavior in both Opera and Firefox, is that you have a Java exploit.  If it was just in Firefox, but not in Opera, then I would suspect a Firefox plugin.  Start an xterm and type (the "$" just means a shell prompt, usually BASH):

$ cd ; file .java

If you get something like this back then Java is installed and active.

.java: directory

If it is there, and assuming you use BASH (you can do unless you chose otherwise) type:

$ rm -f .java/deployment/cache/*
$ rm -f .java/deployment/cache/javapi/*
$ rm -f  .java/deployment/cache/javapi/v1.0/*
$ rm -f .java/deployment/cache/javapi/v1.0/ext/*
$ rm -f .java/deployment/cache/javapi/v1.0/file/*
$ rm -f .java/deployment/cache/javapi/v1.0/jar/*
$ rm -f .java/deployment/cache/javapi/v1.0/tmp/*
$ rm -f .java/deployment/cache/tmp/
#  If it was me, I would just type:
$ rm -fr .java

The other possibility is a Flash Player plugin but Flash isn't supposed to work with Opera and you said the problem also exists in Opera.  But if you try the following and the problem persists then you have a pretty severe problem (make sure you close all browsers):

$ rm -f index*
$ wget google.com
$ gedit index.html &

In the editor, some place there should be a title and it should be Google.  You should also have a:

window.google=...
window.gbar={};...

some place in the file.  If you do, close the editor and remove the file the same way you did before you used wget to get it.  Based on positive results here and your rootkit scan the chances are highly likely the system is fine.  You should NEVER have to sudo for normal web browsing.  That is the only way a rootkit can be installed.  Yes Linux is that much more secure than MS Windows, and OpenBSD is even more secure.  Okay, lets assume you are fine to this point (a good assumption).  Then try the following (remember, during all of this, no browser has been opened and you should NOT open one now).  Now in the xterm type:

$ env | grep PATH | grep -v MAN
# or better yet
$ echo $PATH
This should show your path.  Each folder (directory) is colon ":' separated from every other folder.  So for example:

PATH=/usr/kerberos/sbin:/usr/kerberos/bin

has two folders, /usr/kerberos/sbin, and /usr/kerberos/bin.  You should also have perhaps the following folders:

/bin
/usr/bin
/usr/sbin  # optional
/usr/sbin  # optional
/usr/X11R6/bin
/usr/local/bin
/usr/local/bin
/opt/bin
/home/hhhobbit/bin  # your user name would be different.
.

I do NOT like having "." in the $PATH.  If it is there, I would remove it, or at the very least have it last.  If you don't have your own ${HOME}/bin that is fine.  If you do and you didn't add it, you have what I am looking for - evidence that somebody has installed an auto-login program that may do key logging, etcetera.  To make sure of that you would do a:

$ more .bash_profile
$ more .bashrc

There are some other startup files associated with BASH.  To see all of them type:

$ ls -a | grep bash
.bash_history
.bash_logout

The .bash_logout should be short, but the .bash_history could show any evidence of something starting up, and most of the other files could be associated with startup (there ARE other versions of the BASH start files).  Generally speaking NOTHING should be started running by your BASH startup.  All mine has ever done is set parameters like the following:

.bash_profile:
===========
BASH_ENV=${HOME}/.bashrc
EDITOR=/usr/bin/X11/gvim
LANG=en_US
PATH=${PATH}:${HOME}/bin
MANPATH=/usr/local/share/man:/usr/local/man:/usr/share/man
USERNAME=`/usr/bin/whoami`

export BASH_ENV EDITOR LANG PATH USERNAME MANPATH

.bashrc:
=======
umask 077
alias cp='cp -p'
# alias dns='nslookup -silent'
alias path='env | grep PATH'


NOW, if everything looks okay, try the following in the xterm (you can move them back later if desired) and there will be a "> " continue prompt on all of the lines after the first one.  I just show you want YOU have to type:

$ for DIR in .java .macromedia .mozilla .opera
do
  if [ -d ${DIR} ] ; then
    mv ${DIR} save${DIR}
    echo moved ${DIR}
  else
    echo no such dir ${DIR}
  fi
done

Now start Firefox again.  Now try going to [www.google.com](www.google.com)

You may want to contact me directly.  Just look at this page and deduce the email address:

[http://www.securemecca.com/proxy.txt](http://www.securemecca.com/proxy.txt)

What this sounds like is really a Java nasty, and YES, my hosts file DOES take these into account.  The reason I say Java is:

1. You said the problem is the same in both Opera and Firefox on Ubuntu.  Are you SURE that Opera has the same problem?  Also, Lynx does NOT fill things in for you.  If you want to go to google, then type it out completely:  [http://www.google.com](http://www.google.com)

2. You said the problem does not exist in WIndows.  If you are using a broadband router that rules out a hacked router box but you SHOULD do the following with it if you can and it has wireless provisions:

- use WPA encryption
- change your SSID to something other than the default
- do not broadcast your SSID

In case you are wondering, yes, I have had to torch those folders, and on Linux.  If the problem still exists, it is elsewhere and you can go back to what you had with (close the browsers and start the xterm again):

$ cd
$ for DIR in .java .macromedia .mozilla .opera
do
  if [ -d save${DIR} ] ; then
  rm -fr ${DIR}
  mv save${DIR} ${DIR}
  echo ${DIR} restored
 else
  echo no old ${DIR}  to restore
fi
done

BTW,  Even a linear lookup of 100,000 hosts in a hosts file is infinitely faster than sending a DNS query to a DNS server.  But our (my?) PAC filter chops a lot of wood with very little in CPU time or space.

HHH

---

### Post by Wiebelhaus on 2007-10-17
Great write up HHH.

---

### Post by hhhobbit on 2007-10-18
Merci.  I don't know what to make of what the person said.  It sounds like a red herring to me.  But Linux people need to realize that the following have happened to me and I tighten the browser to not  use Java, use a blocking cookies list, etcetera.  More on the blocked cookies for Firefox later.

1. Due to Gnome being so obliging, they have escaped from the JavaScript sand box and have been able to snatch my email addresses.  Don't be so surprised.  They are in well known files.

2. Installed Java apps to track the mouse, etcetera.   Given the fact I can find the IP address that your machine has with Java (but not yet with JavaScript), that doesn't surprise me.  That is why I have Java disabled by default.  Rather than using NoScript, I strongly urge people use Privoxy instead, unless they want to take all of that info, my stuff, and chuck it into a real proxy server for multiple machines.  I say I don't use Java, but I sometimes have to test certain things, but before I go into the danger zone (read - porn, gambling, and other bad sites) I do the following:

for DIR in adobe java macromedia mozilla opera
do
  rm -f /home/backups/hhhobbit/${DIR}.7z
  7za a /home/backups/hhhobbit/${DIR}.7z ./.${DIR}
done
7za a /home/backups/hhhobbit/bin.7z ./bin

Then I proceed but I always back-track to where I was at after testing is over.  Now what if that user had done this?  We wouldn't be having this conversation would we?  You need to realize that I am a Unix hacker from WAY back there.  We are talking way back before Linux was a gleam in Linus Torvald's eyes people.

3. Also due to the tight nature of Gnome, they HAVE messaged my POP mail client and tried auto-sending out an email message from something I am doing in the browser.  Once they did it from a web mail message.  If I had been quicker on my feet I should have recreated the POP folder and filled it full of addresses headed back to them and set it to auto-login and changed my POP password.   Then I could have filled their email box full with their own trash (as long as I could figure a way to auto-click the link).  After it was all over I would blow away that mail folder, restore mine, and change my POP password back to what it was.

There are just some of the things I have caught them doing and rest assured that with at least 95% of Linux users using BASH, you DO have mini mono-culture.  I looked at the FISH shell but the guy needs to figure out how to eradicate at least some of the strcmp(), et al, and replace the ones that need to be with strncmp(), et al.  He also needs to handle the su and sudo. Don't get me started on sudo because I am strongly in favor of a root login - for things like this , logging in as root, blowing away the user and starting over is highly advisable IF it is as bad as the person says it is. I don't believe it is that bad but it wouldn't be the first time I have been wrong.  By that I mean the FISH creator needs to understand that the memory space for what the sudo/su does and a normal user does needs to be kept separate. But I do NOT think this user (and many others) is appraised of one thing - security is a mind-set and some people just don't seem to get it.  It isn't just one magic bullet.  Sure, Linux is more secure than Windows, but that doesn't excuse you from tightening the browser perms, NEVER going to the Internet as root, etcetera.  On that point, I am providing a list of blocked cookies for Firefox:

[http://www.SecureMecca.com/Firefox.unx.7z](http://www.SecureMecca.com/Firefox.unx.7z)
[http://www/HostsFile.org/Firefox.unx.7z](http://www/HostsFile.org/Firefox.unx.7z)

Sorry, you need to compile it.  I no longer provide the sig, but if requested by a proper OpenPGP encrypted message, I will send it (my key is F9C3CC87).  Given the fact that it is all sitting right there in front of you, why do you need the sig?  Analyze the source.  It is Gnu'd.  I also provide it for Windows in case people are using Firefox portable:

[http://www.SecureMecca.com/Firefox.msw.7z](http://www.SecureMecca.com/Firefox.msw.7z)
[http://www.HostsFile.org/Firefox.msw.7z](http://www.HostsFile.org/Firefox.msw.7z)

The list may be short, but blocking cookies you will never  and / or are not used to track you is a waste of time (but I HAVE caught cookie exploits that attempt to reset your DNS server to something else other than what it was - and that was with wget).  I also dump all cookies when the browser closes.

I hope the person comes back or contacts me directly.  But it is silly to talk about some anti-adware / anti-spyware package for Linux because at this point in time it is not needed.  I do have both Grisoft AVG and ClamAV installed, but their primary purpose is to scan for WINDOWS malware.  I have yet to see these much vaunted viruses for Linux - lots of rootkits, but so far no viruses.  But just consider one thing - there are Windows root-kits where the people do all of the following:

- salt-ciper encryption or similar of the installer to avoid AV / AntiSpy Detection
- alter their binary every day or so, also  to avoid the same AV Detection engines
- refuse to run the installer if it detects that Windows is being run as a VM (run via VMWare)
- there is more - **Trust me!**

Now if you think those people can't do the same to a sloppy Linux box you better think again.  THEY WILL, but only if there is some money in it.  But if you think I can't hack your Linux box, think again - I CAN!  And I just have normal intelligence - wait until the big guns get started.

[B]What I am trying to do is attempting to get the Linux / Mac OS-X people ready for when the perps move over to the 'nix world.  I have probably already failed.
[/B]

Will the original poster please contact me directly?  I need you to zip up stuff to send to me.  I think you are okay, but if the perps are already exploiting the BASH monoculture, both Linux and Mac OS-X people are in real trouble.  If they are, at this stage it is only exploratory, and the Mac OS-X people will be first - "Windows viruses can't hurt OS-X because Linux won't let it" (a user who posted who shall remain anonymous).

Henry Hertz Hobbit

---

### Post by alefnull on 2007-10-31
someone please post if a solution is found.
i'm having basically the same problem...

when i type a keyword into my location bar (regardless of the browser i use, i've tried a few now) it brings me to a 'infospace.com' search results page.

i looked in my about:config and everything is as it should be.

my hosts file looks normal.

even lynx brings me to it every now and then.

EDIT: also, i'm wondering if maybe it has to do with my neighbour's wireless network (which i'm leeching) i'll try taking my laptop to the cafe tomorrow to see if that's the case. like, perhaps they just changed something because this didn't happen up until today. i pray that this is the case, because i'd really like to know that i truly am done with security issues...

---

### Post by alefnull on 2007-11-01
nevermind. i figured out what the problem is for me... not so sure if it's the same for the original poster...
if i type keywords into the location bar, and google doesn't get an absolute positive hit on what i'm looking for, i get a verizon/yahoo search results page. i clicked on About This Page and got this...

> **About the Search Results Page**

                                      You reached the preceding search results page because Verizon is using specific Domain Name              Service (DNS) Servers to look up domain names. These DNS Servers eliminate dead-end              "no such name" error pages you can encounter as you surf the web. This search service is              designed to make your web surfing experience more productive. No software was installed on              your computer for this service to work.


it then goes on to say "if you'd like to opt-out of this service, change the dns settings in your router configuration, blah blah blah"
bummer. since i'm leeching from upstairs neighbours, that means i can't do so. unless i was somehow able to figure out their router password, which is another story altogether.
anyway, sorry for taking up space in this thread.

---

### Post by hhhobbit on 2007-11-02
In that case, stop using their DNS servers and hard configure your machine to use the DNS servers of your choice by putting them in your /etc/resolv.conf file.  You don't need to muck with their broadband router, but like I said, you wouldn't be using mine anyway because here is how it is set:

[LIST=1]
[*]I set the router not to broadcast the SSID.  I do that first.
[*]I change the SSID so it is something other than the default.
[*]I use WPA encryption.
[*]I use an access list.  Unless your MAC address is there, you are not allowed on.
[/LIST]

You should not be going to infospace.com anyway.  I block the following on all systems:

ads.infospace.com
msxml.infospace.com
msxml.180searchassistant.com  # alias to infospace server
msxml.zango.com  # alias ...
web.blowsearch.com  # affiliate

So if they are redirecting you to infospace they are doing you no favors.  Neither are these DNS people and browser people if they pound you through to something - anything.  They need to realize that failure is a good thing.  I would much rather have the browser just give up, rather than asking the DNS server hundreds of times for an IP address for a host name that is no longer in DNS that somebody forgot to remove from their page.  It is causing gray windows of death in Firefox.  If you have it auto-figuring something out for you to go you end up being redirected from the page you initially wanted to go to. Unless they have a setting that allows you to set a default server to go to all the time in that case in the browser (mine would be localhost), it is stupid to keep demanding something from the DNS server forever.  That is why I have the following two rules for thousands of typo hosts:

BadNetworks[i++] = "216.65.41.185, 255.255.255.255";
BadNetworks[i++] = "216.65.41.188,  255.255.255.255";

They are blocking tens of thousands of  typo hosts (syamantec.com).  I suspect one more possibility is that a host may be resetting your  DNS servers with cookies (yes, believe it or not you can see it being attempted with wget).  But unless they have set up the auto NIC config sloppy so that it doesn't demand you sudo to make the change that should not happen.  That is all the more reason to use DNS servers that just tell you the host is dead and NIC parameters that are viewable only by the normal user, settable only by root.  Good luck getting the browser people to go back to that model.  I would rather be told - dead, or you mistyped than being directed some place I didn't want to go to in the first place.  If it is just a sub-portion of the page, ignore it.  When you end up with something like this that is not predictable and takes lots of time to chase down it shows you what they are doing is **wrong**.  But there **are** hosts that can and do track your or do something else bad on Linux.   I have caught them putting in both Java (which is why it is not on by default for me) and JavaScript (which is why I recommend Privoxy) code that fouls things up.  In that case it is sometimes easier to just blow the browser folders away and start over.  I can also write a virus using nothing but shell scripts.  I guess that means the next thing the browser people are going to do is to allow the execution of shell scripts inside the browser as a **service** to us.  Sigh. The first virus was written on either Apple II or Unix depending on what dates you accept.  If somebody starts writing viruses and depend on everybody using BASH (a good reason for me to go back to Korn shell), behavior like this is just going to compound the situation making it even harder to track down.  I have the same view of DHCP any time you go over 2-3 systems.  I much prefer static IP addresses so you can track things down.

---

### Post by Halfling Rogue on 2007-11-04
> **hhhobbit said:**
> The other possibility is a Flash Player plugin


Almost positive I have the same problem with a Flash plugin over [here]("http://ubuntuforums.org/showthread.php?t=602795"). Would I fix it the same way you've told this guy to?

---

### Post by Halfling Rogue on 2007-11-04
Ugh. I ran the rm -rf .java command, and now Firefox won't even let me login to the forums; I have to use Opera. Do I have to reinstall Java with the syn package manager?

---

### Post by rupierto on 2007-11-14
Take a look here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and go down to:

"Browser / Spyware : Java/Flash/Ad-ware/Trackers/Cookies"

---

### Post by Halfling Rogue on 2007-11-14
Oh, awesome. Thank you!

---

### Post by hhhobbit on 2007-11-14
There are some cookies you just don't want set.  Of course, if you block the host in the first place, then they can't set a cookie, can they?  As the last thing you should do with Netscape or Firefox, put a blocked cookie list in place.  I submit mine as a good start (you have to either compile the program or drag the hostperm.1 file into place manually):

[http://www.securemecca.com/Firefox.unx.7z](http://www.securemecca.com/Firefox.unx.7z)
[http://www.hostsfile.org/Firefox.unx.7z](http://www.hostsfile.org/Firefox.unx.7z)

Or if you don't have 7-Zip, I will relent just once and provide a current version as of now in Zip format.  There is no guarantee these files will be updated.

[http://www.securemecca.com/Firefox.unx.zip](http://www.securemecca.com/Firefox.unx.zip)
[http://www.hostsfile.org/Firefox.unx.zip](http://www.hostsfile.org/Firefox.unx.zip)

Why 7-Zip?

15113  Firefox.unx.7z
20270  Firefox.unx.zip

If you have a good hostperm.1 file (blocked cookies, popups, etc.) on Windows, just copy the hostperm.1 file from there to your ~/.mozilla/firefox/XXXXXXXX.default folder.  The XXXXXXXX will be different for everybody, but it is a random sequence of characters [a...z|0...9].

I still don't see how blowing away the .mozilla, .opera, .java, .macromedia, and .adobe or other folders can possibly kill a browser.  It is the primary problem you have on Linux, and it has yet failed to fix the problem for me.  But once you have done that, to prevent having to do it again (I don't want to enter in all of those config changes I make to secure the browser), take these steps here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Only people like me that go into the danger zone all the time need to take extra steps ***(and we do)***. There are spies and hosts like the one I had the other day that forced me to switch to another workspace with an xterm and do a "ps -eadf", find the PIDs and kill the browser.  It had effectively trapped it so I couldn't even close the browser.  The exploit used JavaScript.  Even though the software that would have been injected would only infect a Microsoft Windows system, I blocked the host on both Linux and Unix.  Somebody trapping your browser on Linux to the point that you cannot close it is reason enough for me to block you.  But the difference between our hosts file and the MVPS hosts file is in two parts:

1. We have a PAC filter.  A hosts file entry is like a fine hand saw in a violin making shop.  A PAC filter is the huge cookie-cutter automated band saw chopping out huge swaths of hosts with very little (but you do end up with some false positives).

2. The current list of hosts I am blocking was reduced considerably by using the PAC filter, but even so, I am down to:

  86 add.Porn
 200 add.WinRisk
 168 main

and I have 100 hosts or so to work through in main to see if they fit into either these two or other categories.  Those 200 do NOT go onto Linux since they pose no threat there.  That should give you a good idea of just how much safer Linux is compared to Windows.  You **do** gain a substantial amount of security by just switching from Microsoft Windows to Linux. Just don't stop there.  Tighten things down.  Oh yes, blocking all of those spy hosts speeds up your browsing.  That is what I call a win-win situation.

---

### Post by lazertek on 2007-11-20
use avast to clear malware in your system

---

### Post by lazertek on 2007-12-21
install avast and it will get rid of any malware in the OS.... this should fix it if it hasn't already

---

### Post by hhhobbit on 2007-12-21
Avast isn't very good at getting rid of adware, even on Windows, at least not the free version.  As for Linux ....

1.  There is no registry, ergo there is no place to hide.

2.  Unless you are using something like WINE, none of the Windows binaries (files with .msi, .exe, and .com on the end of them among others) will even run on Ubuntu.  Since 99.99% of all malware are binaries written for Microsoft Windows, Ubuntu should be immune to all of them.  There are a few POC (Proof Of Concept) viruses for Linux, but almost nothing exists in the wild.  The reason why is Unix systems have a combination of System, Owner, Group, and World flags with User, Group, and Other permissions on each of these on every file on the system.  This Mandatory Access Control (MAC) mechanism of the file system makes it almost impossible for viruses for Unix systems to exist in the wild.  It has been this way from the very start for Linux.  You can have Trojans, but there seem to be none.  All malware for Linux seems to be rootkits used to take over a server, plus tools to break in to put the rootkit on.  The rest are these Java and other things like FlashPlayer plugins that can be made to run every time you start the browser.  That is ALL the browser plugins affect too - just the browser.

3. What Avast provides for Linux is the server software for milter in the mail relays.  Nobody even make antivirus stuff for Linux except to handle stuff for Windows.  That means what Avast provides for Linux is not free and since it is meant to scan thousands of email messages it isn't even made for a desktop situation.  It is server software and it is expensive.

4. Other alternatives may be Grisoft AVG, or ClamAV.  As long as you don't have more than one daemon running you can have multiple AV packages on Linux.  These are free.  They also don't detect anything for Linux other than these POC things.  I don't even think they 

This is NOT how you do it on Linux.  What you do is tighten your perms on Firefox and Opera.  I wished these browser vendors would start shipping their stuff out the door cinched down.  Since they don't it is most likely that what the person has is some sort of Firefox extension or a Java app that is doing this to them.  The fast solution is (and you don't need to much around with the installed system stuff!):

1. Bring up a terminal

2. Close all browsers  Make sure NONE of them are running in any workspace.

3. In the terminal, type:

cd
find .mozilla -type f -name bookmarks.html -exec cp -p {} /tmp \;
cp -p .opera/opera6.adr /tmp
rm -fr .mozilla .opera .macromedia .java

4. Fire up the firefox browser, and configure it.  This time make sure Java is turned off.
Exiti Firefox.  If you have Opera, run it and do the same thing.  Make sure the browsers aren't running.

5. In the terminal type:

cd .mozilla/firefox
cat profiles.ini

# observe what it has after the Path=
# it will be a random sequence of 8 alphanumeric chararcters and then a .default
# For example lets say it is a7xh32bz.default . Then you would type:
cd a7xh32bz.default
cp /tmp/bookmarks.html  bookmarks.html
cp /tmp/bookmarks.html  bookmarks.bak
rm -fr bookmarkbackups
mkdir bookmarkbackups

# and if you have Opera
cd
cd .opera
cp /tmp/opera6.adr opera6.adr
cp /tmp/opera6.adr opera6.adr.bak
cd
cat .bash_profile

6.  That should put you back in business.  AFAIK there are NO malware that are OS-centric for Linux except just a few Trojans If there are, then they will be starting themselves in your .bash_profile.  That should get you going in the right direction.  The main thing to rememeber is to tighten the perms of the browser down.  Either use NoScript in Firefox, or turn Java off.  Another alternative is privoxy plus what I have:

[http://www.securemecca.com](http://www.securemecca.com)

Either that or a true proxy server (I don't mean these bust the firewall type proxies) that filters out the bad stuff.  You need it just as much on Linux as you do on Windows.

But almost ALL of the problems you have on Linux will just be in your config files for the browsers.  Until you understand Unix a little better, you won't know that what I am telling you is correct.  It is highly unlikely the malware people are even going to bother with Linux people.  There is no Return On Investment (ROI) to make something for Linux.  That means who ever is making it is doing it just to see how it is done.

I assume the person I originally talked to has resolved their problem.  But all this talk about reinstalling software on Linux is bogus.  You just don't need to do that.  If you don't keep your bookmarks, all you need to do is wipe out the browser config stuff and start over.

---

### Post by slayer04 on 2007-12-21
you are getting the add ware because of Mozilla Firefox not Ubuntu, because Firefox is so popular you are more prone to get add ware but not viruses. to fix I would recommend using another web browser or re-install Firefox

---

