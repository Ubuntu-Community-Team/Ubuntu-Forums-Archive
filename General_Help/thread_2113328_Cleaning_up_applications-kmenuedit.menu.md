---
title: "Cleaning up applications-kmenuedit.menu"
date: 2013-02-07
forum: General Help
---

### Post by Stonecold1995 on 2013-02-07
It seems that every time I use KDE Menu Editor to change the layout of the Kick Start menu, the configuration file (~/.config/menus/applications-kmenuedit.menu) changes.  However, it seems to "fragment" and collect a lot of garbage every time an item is created, moved, changed, or deleted.  This makes it very confusing to read.  Is there any way I can "clean" the file of unnecessary junk that's accumulated?  It's beginning to cause problems, such as one menu entry which refuses to be deleted.

Here's the current contents of the configuration file:
```
<!DOCTYPE Menu PUBLIC '-//freedesktop//DTD Menu 1.0//EN' 'http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd'>
<Menu>
 <Menu>
  <Name>wine-wine</Name>
  <Menu>
   <Name>wine-Programs</Name>
   <Menu>
    <Name>wine-Programs-AVI Joiner</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-MIDInight Express II</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-Accessories</Name>
    <Menu>
     <Name>wine-Programs</Name>
     <NotDeleted/>
    </Menu>
    <Include>
     <Filename>Internet Explorer.desktop</Filename>
     <Filename>Command Prompt.desktop</Filename>
     <Filename>Regedit.desktop</Filename>
     <Filename>Task Manager.desktop</Filename>
     <Filename>Wine File Manager.desktop</Filename>
     <Filename>Wordpad.desktop</Filename>
     <Filename>MSPaint.desktop</Filename>
    </Include>
    <Layout>
     <Merge type="files"/>
     <Filename>wine-notepad.desktop</Filename>
     <Filename>Wine File Manager.desktop</Filename>
     <Filename>Wordpad.desktop</Filename>
     <Filename>MSPaint.desktop</Filename>
     <Filename>Task Manager.desktop</Filename>
     <Filename>Internet Explorer.desktop</Filename>
     <Filename>Command Prompt.desktop</Filename>
     <Filename>Regedit.desktop</Filename>
    </Layout>
   </Menu>
   <Menu>
    <Name>wine-Programs-JazzBuddy</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-Computer Online Forensic Evidence Extractor</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-KeyboardTest</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-PowerISO</Name>
    <Deleted/>
   </Menu>
   <Menu>
    <Name>wine-Programs-SIW</Name>
    <Deleted/>
   </Menu>
   <Layout>
    <Merge type="menus"/>
    <Menuname>wine-Programs-Accessories</Menuname>
   </Layout>
   <Menu>
    <Name>wine-Programs-FAHClient</Name>
    <Deleted/>
   </Menu>
  </Menu>
 </Menu>
 <Menu>
  <Name>Games</Name>
  <Menu>
   <Name>DeSmuME</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>desmume.desktop</Filename>
    <Filename>desmume-glade.desktop</Filename>
   </Layout>
   <Directory>DeSmuME.directory</Directory>
   <Include>
    <Filename>desmume.desktop</Filename>
    <Filename>desmume-glade.desktop</Filename>
   </Include>
  </Menu>
  <Menu>
   <Name>Arcade</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Board</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Kidsgames</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Toys</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>TacticStrategy</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Logic</Name>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Card</Name>
   <Deleted/>
  </Menu>
  <Exclude>
   <Filename>desmume.desktop</Filename>
   <Filename>desmume-glade.desktop</Filename>
   <Filename>Katawa Shoujo.desktop</Filename>
   <Filename>Yume Nikki.desktop</Filename>
   <Filename>Katawa Shoujo-2.desktop</Filename>
   <Filename>fuse-gtk.desktop</Filename>
   <Filename>fuse-sdl.desktop</Filename>
   <Filename>No$GBA.desktop</Filename>
   <Filename>dosbox.desktop</Filename>
   <Filename>fceu.desktop</Filename>
  </Exclude>
  <Include>
   <Filename>Yume Nikki-2.desktop</Filename>
   <Filename>Demonophobia.desktop</Filename>
   <Filename>Katawa Shoujo-3.desktop</Filename>
   <Filename>Planetarian.desktop</Filename>
   <Filename>PennyGirl.desktop</Filename>
   <Filename>Saya no Uta.desktop</Filename>
   <Filename>Swan Song.desktop</Filename>
   <Filename>Wanko to Kurasou.desktop</Filename>
   <Filename>Scarred v0.desktop</Filename>
   <Filename>Narcissu.desktop</Filename>
   <Filename>Uwabami Breakers.desktop</Filename>
   <Filename>Vorpal Rabbit 2.desktop</Filename>
   <Filename>BlankBlood.desktop</Filename>
   <Filename>Crackle Cradle.desktop</Filename>
  </Include>
  <Menu>
   <Name>Katawa Shoujo</Name>
   <Directory>Katawa Shoujo.directory</Directory>
   <Include>
    <Filename>Katawa Shoujo-3.desktop</Filename>
    <Filename>Manual-2.desktop</Filename>
    <Filename>Walkthrough.desktop</Filename>
    <Filename>License.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>Manual.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>License.desktop</Filename>
    <Filename>Walkthrough.desktop</Filename>
    <Filename>Katawa Shoujo-3.desktop</Filename>
    <Filename>Manual-2.desktop</Filename>
   </Layout>
  </Menu>
  <Menu>
   <Name>Yume Nikki</Name>
   <Directory>Yume Nikki.directory</Directory>
   <Include>
    <Filename>Yume Nikki-2.desktop</Filename>
    <Filename>Readme.desktop</Filename>
   </Include>
   <Layout>
    <Merge type="files"/>
    <Filename>Yume Nikki-2.desktop</Filename>
    <Filename>Readme.desktop</Filename>
   </Layout>
   <Exclude>
    <Filename>Vorpal Rabbit 2.desktop</Filename>
   </Exclude>
  </Menu>
  <Menu>
   <Name>PennyGirl</Name>
   <Directory>PennyGirl.directory</Directory>
   <Include>
    <Filename>README.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>Story.desktop</Filename>
    <Filename>Story-2.desktop</Filename>
    <Filename>PennyGirl.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>PennyGirl.desktop</Filename>
    <Filename>README.desktop</Filename>
   </Layout>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Wanko to Kurasou</Name>
   <Directory>Wanko to Kurasou.directory</Directory>
   <Include>
    <Filename>README-5.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>README-2.desktop</Filename>
    <Filename>Wanko to Kurasou.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>Wanko to Kurasou.desktop</Filename>
    <Filename>README-5.desktop</Filename>
   </Layout>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Touhou Project</Name>
   <Directory>Touhou Project-2.directory</Directory>
   <Include>
    <Filename>TH12.desktop</Filename>
    <Filename>TH11 ~ Subterranean Animism.desktop</Filename>
    <Filename>TH08 ~ Imperishable Night.desktop</Filename>
    <Filename>TH09 ~ Phantasmagoria of Flower View.desktop</Filename>
    <Filename>TH09.desktop</Filename>
    <Filename>TH10 ~ Mountain of Faith.desktop</Filename>
    <Filename>TH10.desktop</Filename>
    <Filename>TH12 ~ Undefined Fantastic Object.desktop</Filename>
    <Filename>TH07.desktop</Filename>
    <Filename>Anex86-2.desktop</Filename>
    <Filename>TH06 ~ The Embodiment of Scarlet Devil.desktop</Filename>
    <Filename>TH07 ~ Perfect Cherry Blossom.desktop</Filename>
    <Filename>Music Room.desktop</Filename>
    <Filename>TH12-2.desktop</Filename>
    <Filename>TH12-3.desktop</Filename>
    <Filename>TH13.desktop</Filename>
    <Filename>T98-Next-2.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>Anex86.desktop</Filename>
    <Filename>README-4.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>Anex86-2.desktop</Filename>
    <Filename>T98-Next-2.desktop</Filename>
    <Filename>TH06 ~ The Embodiment of Scarlet Devil.desktop</Filename>
    <Filename>TH07 ~ Perfect Cherry Blossom.desktop</Filename>
    <Filename>TH07.desktop</Filename>
    <Filename>TH08 ~ Imperishable Night.desktop</Filename>
    <Filename>TH09 ~ Phantasmagoria of Flower View.desktop</Filename>
    <Filename>TH09.desktop</Filename>
    <Filename>TH10 ~ Mountain of Faith.desktop</Filename>
    <Filename>TH10.desktop</Filename>
    <Filename>TH11 ~ Subterranean Animism.desktop</Filename>
    <Filename>TH12 ~ Undefined Fantastic Object.desktop</Filename>
    <Filename>TH12.desktop</Filename>
    <Filename>TH12-2.desktop</Filename>
    <Filename>TH12-3.desktop</Filename>
    <Filename>TH13.desktop</Filename>
    <Filename>Music Room.desktop</Filename>
   </Layout>
  </Menu>
  <Menu>
   <Name>DeSmuME-2</Name>
   <Include/>
   <Exclude>
    <Filename>No$GBA.desktop</Filename>
   </Exclude>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Katawa Shoujo-2</Name>
   <NotDeleted/>
   <Layout>
    <Merge type="files"/>
    <Filename>Katawa Shoujo-3.desktop</Filename>
    <Filename>Manual-2.desktop</Filename>
    <Filename>Walkthrough.desktop</Filename>
   </Layout>
   <Exclude>
    <Filename>License.desktop</Filename>
   </Exclude>
   <Include>
    <Filename>Walkthrough.desktop</Filename>
   </Include>
  </Menu>
  <Move>
   <Old>Katawa Shoujo</Old>
   <New>Katawa Shoujo-2</New>
  </Move>
  <Menu>
   <Name>Demonophobia</Name>
   <Directory>Demonophobia.directory</Directory>
   <Include>
    <Filename>README-4.desktop</Filename>
    <Filename>README-6.desktop</Filename>
    <Filename>Walkthrough-2.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>Demonophobia.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>Demonophobia.desktop</Filename>
    <Filename>README-6.desktop</Filename>
    <Filename>Walkthrough-2.desktop</Filename>
   </Layout>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Yume Nikki-2</Name>
   <Exclude>
    <Filename>Yume Nikki-2.desktop</Filename>
    <Filename>Readme.desktop</Filename>
   </Exclude>
   <Include/>
   <Layout/>
   <Menu>
    <Name>Touhou Project</Name>
    <NotDeleted/>
   </Menu>
   <Deleted/>
  </Menu>
  <Move>
   <Old>Yume Nikki</Old>
   <New>Yume Nikki-2</New>
  </Move>
  <Menu>
   <Name>Katawa Shoujo-3</Name>
   <Exclude>
    <Filename>Katawa Shoujo-3.desktop</Filename>
   </Exclude>
   <Deleted/>
  </Menu>
  <Move>
   <Old>Katawa Shoujo-2</Old>
   <New>Katawa Shoujo-3</New>
  </Move>
  <Move>
   <Old>Touhou Project</Old>
   <New>Yume Nikki-2/Touhou Project</New>
  </Move>
  <Menu>
   <Name>Touhou Project-2</Name>
   <NotDeleted/>
  </Menu>
  <Move>
   <Old>Yume Nikki-2/Touhou Project</Old>
   <New>Touhou Project-2</New>
  </Move>
  <Menu>
   <Name>Yume Nikki-3</Name>
   <Deleted/>
  </Menu>
  <Move>
   <Old>Yume Nikki-2</Old>
   <New>Yume Nikki-3</New>
  </Move>
  <Layout>
   <Merge type="files"/>
   <Filename>BlankBlood.desktop</Filename>
   <Filename>Crackle Cradle.desktop</Filename>
   <Filename>Demonophobia.desktop</Filename>
   <Filename>Katawa Shoujo-3.desktop</Filename>
   <Filename>Narcissu.desktop</Filename>
   <Filename>PennyGirl.desktop</Filename>
   <Filename>Planetarian.desktop</Filename>
   <Filename>Saya no Uta.desktop</Filename>
   <Filename>Scarred v0.desktop</Filename>
   <Filename>Swan Song.desktop</Filename>
   <Merge type="menus"/>
   <Menuname>Touhou Project-2</Menuname>
   <Filename>Uwabami Breakers.desktop</Filename>
   <Filename>Wanko to Kurasou.desktop</Filename>
   <Filename>Vorpal Rabbit 2.desktop</Filename>
   <Filename>Yume Nikki-2.desktop</Filename>
  </Layout>
 </Menu>
 <Menu>
  <Name>.hidden</Name>
  <Include>
   <Filename>Oggchan.desktop</Filename>
  </Include>
  <Exclude/>
  <Layout/>
 </Menu>
 <Menu>
  <Name>Internet</Name>
  <Menu>
   <Name>Browsers</Name>
   <Directory>Browsers.directory</Directory>
   <Directory>Browsers-2.directory</Directory>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Browsers-2</Name>
   <Directory>Browsers-3.directory</Directory>
   <Include>
    <Filename>firefox.desktop</Filename>
    <Filename>chromium-browser.desktop</Filename>
    <Filename>Tor Browser.desktop</Filename>
    <Filename>elinks.desktop</Filename>
   </Include>
   <Layout>
    <Merge type="files"/>
    <Filename>Tor Browser.desktop</Filename>
    <Filename>firefox.desktop</Filename>
    <Filename>chromium-browser.desktop</Filename>
    <Filename>elinks.desktop</Filename>
   </Layout>
  </Menu>
  <Exclude>
   <Filename>firefox.desktop</Filename>
   <Filename>chromium-browser.desktop</Filename>
   <Filename>axel-kapt.desktop</Filename>
   <Filename>remmina.desktop</Filename>
   <Filename>elinks.desktop</Filename>
   <Filename>zenmap-2.desktop</Filename>
  </Exclude>
  <Include>
   <Filename>NetTools.desktop</Filename>
  </Include>
  <Layout>
   <Merge type="menus"/>
   <Menuname>Browsers-2</Menuname>
   <Menuname>Terminal</Menuname>
   <Merge type="files"/>
   <Filename>electrum.desktop</Filename>
   <Filename>OpenVAS-Client.desktop</Filename>
   <Filename>JB-javaws.desktop</Filename>
   <Filename>wireshark.desktop</Filename>
   <Filename>zenmap-root.desktop</Filename>
   <Filename>zenmap.desktop</Filename>
   <Filename>google-earth.desktop</Filename>
   <Filename>NetTools.desktop</Filename>
   <Filename>icedtea-netx-javaws.desktop</Filename>
   <Filename>kde4-keditbookmarks.desktop</Filename>
   <Filename>kde4-knetattach.desktop</Filename>
   <Filename>kde4-Kppp.desktop</Filename>
   <Filename>kde4-ktorrent.desktop</Filename>
   <Filename>kvirc.desktop</Filename>
   <Separator/>
   <Menuname>More</Menuname>
  </Layout>
 </Menu>
 <Menu>
  <Name>Education</Name>
  <Menu>
   <Name>Science</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>FAHControl-2.desktop</Filename>
    <Filename>jmol.desktop</Filename>
   </Layout>
   <Include>
    <Filename>FAHControl-2.desktop</Filename>
   </Include>
  </Menu>
  <Menu>
   <Name>Miscellaneous</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>Kindle for PC.desktop</Filename>
   </Layout>
   <Include>
    <Filename>Kindle for PC.desktop</Filename>
   </Include>
  </Menu>
 </Menu>
 <Menu>
  <Name>Applications</Name>
  <Exclude>
   <Filename>FAHControl.desktop</Filename>
   <Filename>DVDFab.desktop</Filename>
   <Filename>DoubleKiller.desktop</Filename>
  </Exclude>
  <Layout>
   <Merge type="files"/>
   <Filename>wine-extension-wim.desktop</Filename>
   <Filename>wine-extension-swm.desktop</Filename>
   <Filename>wine-extension-cab.desktop</Filename>
   <Filename>wine-extension-dmg.desktop</Filename>
   <Filename>wine-extension-bz2.desktop</Filename>
   <Filename>wine-extension-tbz.desktop</Filename>
   <Filename>wine-extension-zip.desktop</Filename>
   <Filename>wine-extension-split.desktop</Filename>
   <Filename>wine-extension-xar.desktop</Filename>
   <Filename>wine-extension-z.desktop</Filename>
   <Filename>wine-extension-tar.desktop</Filename>
   <Filename>wine-extension-tpz.desktop</Filename>
   <Filename>wine-extension-lzh.desktop</Filename>
   <Filename>wine-extension-gzip.desktop</Filename>
   <Filename>wine-extension-arj.desktop</Filename>
   <Filename>wine-extension-gz.desktop</Filename>
   <Filename>wine-extension-lzma.desktop</Filename>
   <Filename>wine-extension-cpio.desktop</Filename>
   <Filename>wine-extension-lha.desktop</Filename>
   <Filename>wine-extension-tbz2.desktop</Filename>
   <Filename>wine-extension-bzip2.desktop</Filename>
   <Filename>wine-extension-tgz.desktop</Filename>
   <Filename>wine-extension-taz.desktop</Filename>
   <Filename>wine-extension-7z.desktop</Filename>
   <Filename>wine-extension-hfs.desktop</Filename>
   <Filename>screensavers-abstractile.desktop</Filename>
   <Filename>screensavers-anemone.desktop</Filename>
   <Filename>screensavers-anemotaxis.desktop</Filename>
   <Filename>screensavers-apollonian.desktop</Filename>
   <Filename>screensavers-apple2.desktop</Filename>
   <Filename>screensavers-attraction.desktop</Filename>
   <Filename>screensavers-barcode.desktop</Filename>
   <Filename>screensavers-blaster.desktop</Filename>
   <Filename>screensavers-blitspin.desktop</Filename>
   <Filename>screensavers-bouboule.desktop</Filename>
   <Filename>screensavers-boxfit.desktop</Filename>
   <Filename>screensavers-braid.desktop</Filename>
   <Filename>screensavers-bumps.desktop</Filename>
   <Filename>screensavers-ccurve.desktop</Filename>
   <Filename>screensavers-celtic.desktop</Filename>
   <Filename>screensavers-cloudlife.desktop</Filename>
   <Filename>screensavers-compass.desktop</Filename>
   <Filename>screensavers-coral.desktop</Filename>
   <Filename>screensavers-crystal.desktop</Filename>
   <Filename>screensavers-cwaves.desktop</Filename>
   <Filename>screensavers-cynosure.desktop</Filename>
   <Filename>screensavers-decayscreen.desktop</Filename>
   <Filename>screensavers-deco.desktop</Filename>
   <Filename>screensavers-deluxe.desktop</Filename>
   <Filename>screensavers-demon.desktop</Filename>
   <Filename>screensavers-discrete.desktop</Filename>
   <Filename>screensavers-distort.desktop</Filename>
   <Filename>screensavers-drift.desktop</Filename>
   <Filename>screensavers-electricsheep.desktop</Filename>
   <Filename>screensavers-epicycle.desktop</Filename>
   <Filename>screensavers-eruption.desktop</Filename>
   <Filename>screensavers-euler2d.desktop</Filename>
   <Filename>screensavers-fadeplot.desktop</Filename>
   <Filename>screensavers-fireworkx.desktop</Filename>
   <Filename>screensavers-flame.desktop</Filename>
   <Filename>screensavers-flow.desktop</Filename>
   <Filename>screensavers-fluidballs.desktop</Filename>
   <Filename>screensavers-fontglide.desktop</Filename>
   <Filename>screensavers-galaxy.desktop</Filename>
   <Filename>screensavers-goop.desktop</Filename>
   <Filename>screensavers-grav.desktop</Filename>
   <Filename>screensavers-greynetic.desktop</Filename>
   <Filename>screensavers-halftone.desktop</Filename>
   <Filename>screensavers-halo.desktop</Filename>
   <Filename>screensavers-helix.desktop</Filename>
   <Filename>screensavers-hopalong.desktop</Filename>
   <Filename>screensavers-ifs.desktop</Filename>
   <Filename>screensavers-imsmap.desktop</Filename>
   <Filename>screensavers-interaggregate.desktop</Filename>
   <Filename>screensavers-interference.desktop</Filename>
   <Filename>screensavers-intermomentary.desktop</Filename>
   <Filename>screensavers-julia.desktop</Filename>
   <Filename>screensavers-kaleidescope.desktop</Filename>
   <Filename>screensavers-kumppa.desktop</Filename>
   <Filename>screensavers-lcdscrub.desktop</Filename>
   <Filename>screensavers-loop.desktop</Filename>
   <Filename>screensavers-m6502.desktop</Filename>
   <Filename>screensavers-maze.desktop</Filename>
   <Filename>screensavers-memscroller.desktop</Filename>
   <Filename>screensavers-metaballs.desktop</Filename>
   <Filename>screensavers-moire.desktop</Filename>
   <Filename>screensavers-moire2.desktop</Filename>
   <Filename>screensavers-mountain.desktop</Filename>
   <Filename>screensavers-munch.desktop</Filename>
   <Filename>screensavers-nerverot.desktop</Filename>
   <Filename>screensavers-noseguy.desktop</Filename>
   <Filename>screensavers-pacman.desktop</Filename>
   <Filename>screensavers-pedal.desktop</Filename>
   <Filename>screensavers-penetrate.desktop</Filename>
   <Filename>screensavers-penrose.desktop</Filename>
   <Filename>kde4-korganizer-import.desktop</Filename>
   <Filename>screensavers-petri.desktop</Filename>
   <Filename>screensavers-phosphor.desktop</Filename>
   <Filename>screensavers-piecewise.desktop</Filename>
   <Filename>screensavers-polyominoes.desktop</Filename>
   <Filename>screensavers-pong.desktop</Filename>
   <Filename>screensavers-pyro.desktop</Filename>
   <Filename>screensavers-qix.desktop</Filename>
   <Filename>screensavers-rd-bomb.desktop</Filename>
   <Filename>screensavers-ripples.desktop</Filename>
   <Filename>screensavers-rocks.desktop</Filename>
   <Filename>screensavers-rorschach.desktop</Filename>
   <Filename>screensavers-rotzoomer.desktop</Filename>
   <Filename>screensavers-shadebobs.desktop</Filename>
   <Filename>screensavers-sierpinski.desktop</Filename>
   <Filename>screensavers-slidescreen.desktop</Filename>
   <Filename>screensavers-slip.desktop</Filename>
   <Filename>screensavers-sonar.desktop</Filename>
   <Filename>screensavers-speedmine.desktop</Filename>
   <Filename>screensavers-spotlight.desktop</Filename>
   <Filename>screensavers-squiral.desktop</Filename>
   <Filename>screensavers-starfish.desktop</Filename>
   <Filename>screensavers-strange.desktop</Filename>
   <Filename>screensavers-substrate.desktop</Filename>
   <Filename>screensavers-swirl.desktop</Filename>
   <Filename>screensavers-thornbird.desktop</Filename>
   <Filename>screensavers-triangle.desktop</Filename>
   <Filename>screensavers-truchet.desktop</Filename>
   <Filename>screensavers-twang.desktop</Filename>
   <Filename>screensavers-vermiculate.desktop</Filename>
   <Filename>screensavers-vidwhacker.desktop</Filename>
   <Filename>vlc-2.desktop</Filename>
   <Filename>screensavers-wander.desktop</Filename>
   <Filename>screensavers-whirlwindwarp.desktop</Filename>
   <Filename>wine-3.desktop</Filename>
   <Filename>screensavers-wormhole.desktop</Filename>
   <Filename>screensavers-xanalogtv.desktop</Filename>
   <Filename>screensavers-xflame.desktop</Filename>
   <Filename>screensavers-xjack.desktop</Filename>
   <Filename>screensavers-xlyap.desktop</Filename>
   <Filename>screensavers-xmatrix.desktop</Filename>
   <Filename>screensavers-xrayswarm.desktop</Filename>
   <Filename>screensavers-xspirograph.desktop</Filename>
   <Filename>screensavers-zoom.desktop</Filename>
   <Filename>kde4-accountwizard.desktop</Filename>
   <Filename>screensavers-antspotlight.desktop</Filename>
   <Filename>wine-extension-zx.desktop</Filename>
   <Filename>wine-extension-sna.desktop</Filename>
   <Filename>wine-extension-sit.desktop</Filename>
   <Filename>wine-extension-tap.desktop</Filename>
   <Filename>wine-extension-fdi.desktop</Filename>
   <Filename>wine-extension-scl.desktop</Filename>
   <Filename>wine-extension-udi.desktop</Filename>
   <Filename>wine-extension-trd.desktop</Filename>
   <Filename>wine-extension-hdi.desktop</Filename>
   <Filename>wine-extension-ezx.desktop</Filename>
   <Filename>wine-extension-msp.desktop</Filename>
   <Filename>wine-extension-sp.desktop</Filename>
   <Filename>wine-extension-fdd.desktop</Filename>
   <Filename>wine-extension-td0.desktop</Filename>
   <Filename>wine-extension-z80.desktop</Filename>
   <Filename>screensavers-fiberlamp.desktop</Filename>
   <Filename>screensavers-fuzzyflakes.desktop</Filename>
   <Filename>screensavers-glblur.desktop</Filename>
   <Filename>screensavers-glcells.desktop</Filename>
   <Filename>screensavers-glmatrix.desktop</Filename>
   <Filename>screensavers-glschool.desktop</Filename>
   <Filename>screensavers-glslideshow.desktop</Filename>
   <Filename>screensavers-gltext.desktop</Filename>
   <Filename>wine-extension-chm.desktop</Filename>
   <Filename>screensavers-hypertorus.desktop</Filename>
   <Filename>gnome-keyring-prompt.desktop</Filename>
   <Filename>kde4-kmailservice.desktop</Filename>
   <Filename>kde4-konsole.desktop</Filename>
   <Filename>kde4-ktelnetservice.desktop</Filename>
   <Filename>mono-runtime.desktop</Filename>
   <Filename>mono-runtime-terminal.desktop</Filename>
   <Filename>wine-extension-ini.desktop</Filename>
   <Filename>wine-extension-txt.desktop</Filename>
   <Filename>openjdk-6-java.desktop</Filename>
   <Filename>openjdk-7-java.desktop</Filename>
   <Filename>apport-kde-mime.desktop</Filename>
   <Filename>wine-extension-url.desktop</Filename>
   <Filename>wine-Programs-Wanko to Kurasou English-Uninstall.desktop</Filename>
   <Filename>wine-Programs-Yume Nikki 0.10 English v3-Uninstall Yume Nikki.desktop</Filename>
   <Filename>gcr-viewer.desktop</Filename>
   <Filename>wine-Programs-Wanko to Kurasou English-View Readme.desktop</Filename>
   <Filename>kde4-kwalletmanager-kwalletd.desktop</Filename>
   <Filename>wine-Programs-Wanko to Kurasou English-Wanko to Kurasou English.desktop</Filename>
   <Filename>wine-extension-rar.desktop</Filename>
   <Filename>wine-2.desktop</Filename>
   <Filename>wine-extension-mfp.desktop</Filename>
   <Filename>wine-extension-html.desktop</Filename>
   <Filename>wine-extension-xml.desktop</Filename>
   <Filename>wine-extension-htm.desktop</Filename>
   <Filename>wine-extension-jpeg.desktop</Filename>
   <Filename>wine-extension-jpg.desktop</Filename>
   <Filename>wine-extension-png.desktop</Filename>
   <Filename>wine-extension-gif.desktop</Filename>
   <Filename>wine-extension-jfif.desktop</Filename>
   <Filename>wine-extension-jpe.desktop</Filename>
   <Filename>wine.desktop</Filename>
   <Filename>wine-extension-hlp.desktop</Filename>
   <Filename>wine-extension-wri.desktop</Filename>
   <Filename>wine-extension-rtf.desktop</Filename>
   <Filename>wine-Programs-Yume Nikki 0.10 English v3-Yume Nikki.desktop</Filename>
  </Layout>
  <Include/>
 </Menu>
 <Menu>
  <Name>Emulators</Name>
  <Menu>
   <Name>DeSmuME</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>desmume-2.desktop</Filename>
    <Filename>desmume-glade-2.desktop</Filename>
   </Layout>
   <NotDeleted/>
   <Directory>DeSmuME-2.directory</Directory>
   <Include>
    <Filename>desmume-2.desktop</Filename>
    <Filename>desmume-glade-2.desktop</Filename>
   </Include>
  </Menu>
  <Directory>Emulators.directory</Directory>
  <Include>
   <Filename>No$GBA-2.desktop</Filename>
   <Filename>Mini vMac.desktop</Filename>
   <Filename>Anex86-3.desktop</Filename>
   <Filename>Speccy-2.desktop</Filename>
   <Filename>dosbox.desktop</Filename>
   <Filename>Anex86-2.desktop</Filename>
   <Filename>T98-Next.desktop</Filename>
   <Filename>FCE Ultra.desktop</Filename>
  </Include>
  <Exclude>
   <Filename>desmume-2.desktop</Filename>
   <Filename>desmume-glade-2.desktop</Filename>
   <Filename>Speccy.desktop</Filename>
   <Filename>DeSmuME.desktop</Filename>
  </Exclude>
  <Menu>
   <Name>DeSmuME-2</Name>
   <Deleted/>
  </Menu>
  <Move>
   <Old>DeSmuME</Old>
   <New>DeSmuME-2</New>
  </Move>
  <Menu>
   <Name>Fuse Spectrum Emulator</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>fuse-gtk.desktop</Filename>
    <Filename>fuse-sdl.desktop</Filename>
   </Layout>
   <Directory>Fuse Spectrum Emulator.directory</Directory>
   <Include>
    <Filename>fuse-gtk.desktop</Filename>
    <Filename>fuse-sdl.desktop</Filename>
   </Include>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>Speccy</Name>
   <Directory>Speccy.directory</Directory>
   <Include>
    <Filename>Speccy.desktop</Filename>
    <Filename>README-3.desktop</Filename>
   </Include>
   <Exclude/>
   <Layout>
    <Merge type="files"/>
    <Filename>Speccy.desktop</Filename>
    <Filename>README-3.desktop</Filename>
   </Layout>
   <Deleted/>
  </Menu>
  <Menu>
   <Name>DeSmuME-3</Name>
   <Layout>
    <Merge type="files"/>
    <Filename>DeSmuME.desktop</Filename>
    <Filename>DeSmuME (Linux).desktop</Filename>
   </Layout>
   <Directory>DeSmuME-3.directory</Directory>
   <Include>
    <Filename>DeSmuME.desktop</Filename>
    <Filename>DeSmuME (Linux).desktop</Filename>
   </Include>
   <Exclude>
    <Filename>DeSmuME (Windows).desktop</Filename>
   </Exclude>
  </Menu>
  <Layout>
   <Merge type="files"/>
   <Filename>Anex86-2.desktop</Filename>
   <Filename>T98-Next.desktop</Filename>
   <Filename>FCE Ultra.desktop</Filename>
   <Filename>Speccy-2.desktop</Filename>
   <Filename>dosbox.desktop</Filename>
   <Filename>Mini vMac.desktop</Filename>
   <Filename>No$GBA-2.desktop</Filename>
   <Merge type="menus"/>
   <Menuname>DeSmuME-3</Menuname>
  </Layout>
 </Menu>
 <Move>
  <Old>Games/DeSmuME</Old>
  <New>Emulators/DeSmuME</New>
 </Move>
 <Move>
  <Old>Emulators/DeSmuME</Old>
  <New>Games/DeSmuME-2</New>
 </Move>
 <Include/>
 <Exclude>
  <Filename>Speccy.desktop</Filename>
  <Filename>Crackle Cradle.desktop</Filename>
 </Exclude>
 <Menu>
  <Name>Utilities</Name>
  <Menu>
   <Name>wine-Programs</Name>
   <NotDeleted/>
  </Menu>
  <Menu>
   <Name>Icon Extracter</Name>
   <Directory>Icon Extracter.directory</Directory>
   <Include>
    <Filename>Help.desktop</Filename>
    <Filename>Icon Extractor.desktop</Filename>
    <Filename>Help-2.desktop</Filename>
   </Include>
   <Exclude>
    <Filename>DoubleKiller.desktop</Filename>
   </Exclude>
   <Layout>
    <Merge type="files"/>
    <Filename>Icon Extractor.desktop</Filename>
    <Filename>Help-2.desktop</Filename>
   </Layout>
  </Menu>
  <Layout>
   <Merge type="menus"/>
   <Menuname>Icon Extracter</Menuname>
   <Menuname>XUtilities</Menuname>
   <Merge type="files"/>
   <Filename>kde4-kmousetool.desktop</Filename>
   <Filename>DoubleKiller.desktop</Filename>
   <Filename>kde4-knotes.desktop</Filename>
   <Filename>kde4-kmag.desktop</Filename>
   <Filename>kde4-kate.desktop</Filename>
   <Filename>kde4-akonaditray.desktop</Filename>
   <Filename>kde4-ark.desktop</Filename>
   <Filename>kde4-klipper.desktop</Filename>
   <Filename>kde4-kfontview.desktop</Filename>
   <Filename>virtualbox.desktop</Filename>
   <Filename>gksu.desktop</Filename>
   <Filename>kde4-kcalc.desktop</Filename>
   <Filename>kde4-ktesnippets_editor.desktop</Filename>
   <Filename>sysinfo.desktop</Filename>
   <Filename>kde4-synaptiks.desktop</Filename>
   <Filename>truecrypt.desktop</Filename>
   <Filename>kde4-kvkbd.desktop</Filename>
   <Menuname>wine-Programs</Menuname>
   <Separator/>
   <Menuname>More</Menuname>
  </Layout>
  <Menu>
   <Name>XUtilities</Name>
   <Layout/>
   <Include/>
   <Exclude>
    <Filename>DoubleKiller.desktop</Filename>
   </Exclude>
  </Menu>
  <Include>
   <Filename>DoubleKiller.desktop</Filename>
  </Include>
  <Exclude/>
 </Menu>
 <Move>
  <Old>wine-wine/wine-Programs/wine-Programs-7-Zip</Old>
  <New>Utilities/wine-Programs</New>
 </Move>
 <Move>
  <Old>Utilities/wine-Programs</Old>
  <New>wine-wine/wine-Programs/wine-Programs-Accessories/wine-Programs</New>
 </Move>
 <Move>
  <Old>wine-wine/wine-Programs/wine-Programs-Accessories/wine-Programs</Old>
  <New>Utilities/wine-Programs</New>
 </Move>
 <Menu>
  <Name>Development</Name>
  <Layout>
   <Merge type="files"/>
   <Filename>Win32Dasm.desktop</Filename>
   <Merge type="menus"/>
   <Menuname>Translation</Menuname>
   <Menuname>Web Development</Menuname>
   <Menuname>X-KDE-KDevelopIDE</Menuname>
   <Filename>kde4-kdbg.desktop</Filename>
   <Filename>kde4-kompare.desktop</Filename>
   <Filename>bless.desktop</Filename>
   <Filename>monodevelop.desktop</Filename>
   <Filename>python2.6.desktop</Filename>
   <Filename>python2.7.desktop</Filename>
  </Layout>
  <Include>
   <Filename>Win32Dasm.desktop</Filename>
  </Include>
 </Menu>
 <Menu>
  <Name>Multimedia</Name>
  <Include>
   <Filename>DVDFab.desktop</Filename>
   <Filename>Sothink SWF Decompiler.desktop</Filename>
  </Include>
  <Exclude>
   <Filename>Oggchan.desktop</Filename>
  </Exclude>
  <Menu>
   <Name>Utilities</Name>
   <NotDeleted/>
  </Menu>
  <Layout>
   <Merge type="files"/>
   <Filename>aegisub.desktop</Filename>
   <Filename>ghb.desktop</Filename>
   <Filename>isomaster.desktop</Filename>
   <Filename>pulseaudio-equalizer.desktop</Filename>
   <Filename>qjackctl.desktop</Filename>
   <Filename>gtk-recordmydesktop.desktop</Filename>
   <Filename>timidity-interfaces-extra.desktop</Filename>
   <Filename>Sothink SWF Decompiler.desktop</Filename>
   <Filename>smplayer_enqueue.desktop</Filename>
   <Filename>smplayer.desktop</Filename>
   <Filename>mkvmergeGUI.desktop</Filename>
   <Filename>mkvinfo.desktop</Filename>
   <Filename>kde4-k3b.desktop</Filename>
   <Filename>vlc.desktop</Filename>
   <Filename>audacity.desktop</Filename>
   <Filename>kde4-kmix.desktop</Filename>
   <Filename>Kino.desktop</Filename>
   <Filename>DVDFab.desktop</Filename>
   <Separator/>
   <Merge type="menus"/>
   <Menuname>More</Menuname>
  </Layout>
 </Menu>
 <Menu>
  <Name>Utilities-2</Name>
  <NotDeleted/>
 </Menu>
 <Move>
  <Old>Utilities</Old>
  <New>Utilities-2</New>
 </Move>
 <Move>
  <Old>Utilities-2</Old>
  <New>Multimedia/Utilities</New>
 </Move>
 <Move>
  <Old>Multimedia/Utilities</Old>
  <New>Utilities-2</New>
 </Move>
 <Menu>
  <Name>Settingsmenu</Name>
  <Layout>
   <Merge type="files"/>
   <Filename>bum.desktop</Filename>
   <Filename>kde4-kdepasswd.desktop</Filename>
   <Filename>itweb-settings.desktop</Filename>
   <Filename>im-switch.desktop</Filename>
   <Filename>kde4-kdesystemsettings.desktop</Filename>
   <Filename>kde4-kmenuedit.desktop</Filename>
   <Filename>openjdk-6-policytool.desktop</Filename>
   <Filename>openjdk-7-policytool.desktop</Filename>
   <Filename>seahorse.desktop</Filename>
   <Filename>xscreensaver-properties.desktop</Filename>
   <Filename>software-properties-gtk.desktop</Filename>
   <Filename>software-properties-kde.desktop</Filename>
   <Filename>synaptic.desktop</Filename>
   <Filename>kde4-systemsettings.desktop</Filename>
  </Layout>
  <Menu>
   <Name>Science</Name>
   <NotDeleted/>
  </Menu>
 </Menu>
 <Menu>
  <Name>Utilities-3</Name>
  <NotDeleted/>
 </Menu>
 <Move>
  <Old>Utilities-2</Old>
  <New>Utilities-3</New>
 </Move>
 <Menu>
  <Name>Science</Name>
  <NotDeleted/>
  <Layout/>
  <Menu>
   <Name>Office</Name>
   <NotDeleted/>
  </Menu>
 </Menu>
 <Move>
  <Old>Science</Old>
  <New>Settingsmenu/Science</New>
 </Move>
 <Move>
  <Old>Settingsmenu/Science</Old>
  <New>Science</New>
 </Move>
 <Menu>
  <Name>Utilities-4</Name>
  <NotDeleted/>
  <Include>
   <Filename>Duplicate Photo Finder.desktop</Filename>
   <Filename>7-zip.desktop</Filename>
  </Include>
  <Layout>
   <Merge type="files"/>
   <Filename>gvim.desktop</Filename>
   <Filename>kde4-jovieapp.desktop</Filename>
   <Filename>kde4-kmouth.desktop</Filename>
   <Filename>kde4-nepomukbackup.desktop</Filename>
   <Filename>Duplicate Photo Finder.desktop</Filename>
   <Merge type="menus"/>
   <Menuname>Icon Extracter</Menuname>
   <Menuname>XUtilities</Menuname>
   <Filename>PeaZip.desktop</Filename>
   <Filename>7-zip.desktop</Filename>
   <Filename>palimpsest.desktop</Filename>
   <Filename>OpenVAS-Client.desktop</Filename>
   <Filename>kde4-kshutdown.desktop</Filename>
   <Filename>clamtk.desktop</Filename>
   <Filename>kde4-kmousetool.desktop</Filename>
   <Filename>DoubleKiller.desktop</Filename>
   <Filename>kde4-knotes.desktop</Filename>
   <Filename>kde4-kmag.desktop</Filename>
   <Filename>kde4-kate.desktop</Filename>
   <Filename>kde4-akonaditray.desktop</Filename>
   <Filename>kde4-ark.desktop</Filename>
   <Filename>kde4-klipper.desktop</Filename>
   <Filename>kde4-kfontview.desktop</Filename>
   <Filename>virtualbox.desktop</Filename>
   <Filename>gksu.desktop</Filename>
   <Filename>kde4-kcalc.desktop</Filename>
   <Filename>kde4-ktesnippets_editor.desktop</Filename>
   <Filename>sysinfo.desktop</Filename>
   <Filename>kde4-synaptiks.desktop</Filename>
   <Filename>truecrypt.desktop</Filename>
   <Filename>kde4-kvkbd.desktop</Filename>
   <Separator/>
   <Menuname>More</Menuname>
  </Layout>
  <Menu>
   <Name>XUtilities</Name>
   <Layout/>
   <Include/>
   <Exclude>
    <Filename>7-zip.desktop</Filename>
   </Exclude>
  </Menu>
  <Menu>
   <Name>wine-Programs</Name>
   <Deleted/>
  </Menu>
  <Exclude/>
 </Menu>
 <Move>
  <Old>Utilities-3</Old>
  <New>Utilities-4</New>
 </Move>
 <Menu>
  <Name>Office</Name>
  <NotDeleted/>
  <Layout>
   <Merge type="files"/>
   <Filename>libreoffice-calc.desktop</Filename>
   <Filename>libreoffice-draw.desktop</Filename>
   <Filename>libreoffice-impress.desktop</Filename>
   <Filename>libreoffice-math.desktop</Filename>
   <Filename>libreoffice-startcenter.desktop</Filename>
   <Filename>libreoffice-writer.desktop</Filename>
   <Filename>kde4-okular.desktop</Filename>
   <Separator/>
   <Merge type="menus"/>
   <Menuname>More</Menuname>
  </Layout>
  <Exclude>
   <Filename>kde4-calligra.desktop</Filename>
   <Filename>bitcoin-qt.desktop</Filename>
   <Filename>kde4-kexi.desktop</Filename>
   <Filename>kde4-kontact-admin.desktop</Filename>
   <Filename>kde4-Kontact.desktop</Filename>
  </Exclude>
 </Menu>
 <Move>
  <Old>Office</Old>
  <New>Science/Office</New>
 </Move>
 <Move>
  <Old>Science/Office</Old>
  <New>Office</New>
 </Move>
 <Menu>
  <Name>Yume Nikki</Name>
  <NotDeleted/>
 </Menu>
 <Move>
  <Old>Games/Yume Nikki-2</Old>
  <New>Yume Nikki</New>
 </Move>
 <Move>
  <Old>Yume Nikki</Old>
  <New>Games/Yume Nikki-2</New>
 </Move>
 <Layout>
  <Merge type="menus"/>
  <Menuname>Emulators</Menuname>
  <Menuname>Debian</Menuname>
  <Menuname>Development</Menuname>
  <Menuname>Education</Menuname>
  <Menuname>Games</Menuname>
  <Menuname>Graphics</Menuname>
  <Menuname>.hidden</Menuname>
  <Menuname>Internet</Menuname>
  <Menuname>Multimedia</Menuname>
  <Menuname>Utilities-4</Menuname>
  <Menuname>Office</Menuname>
  <Menuname>Science</Menuname>
  <Menuname>Settingsmenu</Menuname>
  <Menuname>System</Menuname>
  <Menuname>wine-wine</Menuname>
  <Menuname>Applications</Menuname>
  <Merge type="files"/>
  <Filename>kde4-Help.desktop</Filename>
 </Layout>
</Menu>

```

---

