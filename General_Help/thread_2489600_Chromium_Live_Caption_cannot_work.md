---
title: "Chromium Live Caption cannot work"
date: 2023-08-04
forum: General Help
---

### Post by ctc8631 on 2023-08-04
I have a computer with ubuntu22.04
In google-chrome, I can enable the function 'Live Caption' and it works well with every video, such as youtube.

Then I change to use chromium(115.0.5790.110). It will also download some library when I enable the 'Live Caption' from Settings/Accessibility/Captions' 
But it shows nothing different when I watch a youtube video. Just like no this function(no caption block and no caption). Does anyone have the same problem with. Is there any way to enable it or fix it?

Thans you


The log below is when I open chromium by terminal and watch a video. But I have no idea it will help or not.
```
```

I0000 00:00:1691002185.444765   48506 soda_async_impl.cc:353] Creating soda_impl.
I0000 00:00:1691002185.446259   48506 soda_impl.cc:342] Maximum audio history: 30s
I0000 00:00:1691002185.446295   48506 soda_impl.cc:387] Adding Resampler from 44100 to 16000
I0000 00:00:1691002185.446609   48506 soda_impl.cc:595] Enabling power evaluator.
I0000 00:00:1691002185.446645   48506 soda_impl.cc:605] Adding preamble processor.
I0000 00:00:1691002185.446653   48506 soda_impl.cc:632] Enabling On Device ASR
I0000 00:00:1691002185.468158   48506 terse_processor.cc:622] LP details: [locale: en-us, version: 3007, config file: /home/XXX/snap/chromium/common/chromium/SODALanguagePacks/en-US/1.0.3/SODAModels/configs/ONDEVICE_MEDIUM_CONTINUOUS.config, personalized resources dir: <NONE>]
I0000 00:00:1691002185.470522   48506 terse_processor.cc:216] Loaded PipelineDef.
I0000 00:00:1691002185.547916   48506 terse_processor.cc:233] Initialized ResourceManager.
I0000 00:00:1691002185.548226   48506 terse_processor.cc:245] Initialized GoogleRecognizer.
W0000 00:00:1691002185.567925   48506 terse_processor.cc:352] TISID disabled.
I0000 00:00:1691002185.567939   48506 terse_processor.cc:1317] Domain: CAPTION
W0000 00:00:1691002185.571094   48506 snapshot.cc:41] Failed to get any snapshot revision for |auto-apps| (scope: 15136313109896498463). Error: NOT_FOUND: No candidate revision in snapshot for |auto-apps| (scope: 15136313109896498463)
=== Source Location Trace: ===
speech/service/context/device/framework/snapshot.cc:64
I0000 00:00:1691002185.575373   48506 terse_processor.cc:2561] Resetting Terse Processor with reason: 5
I0000 00:00:1691002185.575436   48506 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002185.575489   48554 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575490   48552 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575492   48549 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575599   48560 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575822   48555 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575842   48548 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575929   48559 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.575956   48562 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.576056   48551 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.576222   48561 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.576334   48558 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.576514   48506 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
I0000 00:00:1691002185.577137   48506 terse_processor.cc:1356] Setup completed
I0000 00:00:1691002185.577159   48506 soda_impl.cc:722] Server ASR Disabled
I0000 00:00:1691002185.577168   48506 soda_impl.cc:798] Initializing audio logger
I0000 00:00:1691002185.577184   48506 soda_async_impl.cc:517] Will attempt to run SODA at thread priority 0
I0000 00:00:1691002185.577201   48506 soda_async_impl.cc:621] SODA session starting (require_hotword:0, hotword_timeout_in_millis:0, trigger_type:TRIGGER_TYPE_UNSPECIFIED, hybrid_asr_config.mode:MODE_DEFAULT)
I0000 00:00:1691002185.577312   48506 soda_async_impl.cc:910] Session parameters updated. Reconfiguring SODA.
I0000 00:00:1691002185.577333   48506 terse_processor.cc:2172] Setting impersonated speaker id to: <NONE>
I0000 00:00:1691002185.577577   48541 soda_async_impl.cc:1518] SODA received first mic audio buffer, size in bytes: 1764, format: 1, channels: 1, : sample rate: 44100
I0000 00:00:1691002185.577636   48541 terse_processor.cc:2391] No terse session, starting a new one on input audio.
W0000 00:00:1691002185.577858   48541 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002185.581754   48568 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002186.086022   48541 soda_async_impl.cc:1226] Not receiving any loopback audio in 500ms. Last audio received time: 0, Current time in us: 1691002186086021
W0000 00:00:1691002186.972769   48571 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002186.974359   48567 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002186.974447   48567 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002187.001734   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002187.001773   48541 terse_processor.cc:3116] Audio pin advanced by: 840ms
I0000 00:00:1691002187.001796   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002187.001802   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002187.002394   48578 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002187.003836   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
W0000 00:00:1691002187.015113   48589 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.176237   48591 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.177213   48584 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002188.177260   48584 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002188.181739   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002188.181759   48541 terse_processor.cc:3116] Audio pin advanced by: 840ms
I0000 00:00:1691002188.181773   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002188.181779   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002188.181842   48593 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.182350   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
I0000 00:00:1691002188.182946   48541 terse_processor.cc:1394] Skip duration: 18.1875ms
W0000 00:00:1691002188.185784   48606 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.735827   48611 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.736400   48607 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002188.736429   48607 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002188.737318   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002188.737326   48541 terse_processor.cc:3116] Audio pin advanced by: 839.9995ms
I0000 00:00:1691002188.737337   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002188.737339   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002188.737447   48608 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002188.737899   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
W0000 00:00:1691002188.741434   48634 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002189.504265   48639 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002189.505488   48633 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002189.505541   48633 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002189.528322   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002189.528342   48541 terse_processor.cc:3116] Audio pin advanced by: 840ms
I0000 00:00:1691002189.528357   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002189.528362   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002189.528548   48635 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002189.529563   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
W0000 00:00:1691002189.537222   48653 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002190.375924   48656 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002190.378241   48651 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002190.378342   48651 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002190.411184   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002190.411208   48541 terse_processor.cc:3116] Audio pin advanced by: 840ms
I0000 00:00:1691002190.411228   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002190.411231   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002190.411588   48655 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002190.413244   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
W0000 00:00:1691002190.419516   48673 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.204440   48671 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.206248   48668 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002191.206316   48668 terse_processor.cc:872] Final recognition has been created.
I0000 00:00:1691002191.222105   48541 terse_processor.cc:2804] TerseProcessor HasRecognitionEvent With Final
I0000 00:00:1691002191.222126   48541 terse_processor.cc:3116] Audio pin advanced by: 840ms
I0000 00:00:1691002191.222142   48541 terse_processor.cc:3179] Longform resets session because this session is 840ms long.
I0000 00:00:1691002191.222146   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002191.222360   48669 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.223338   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
W0000 00:00:1691002191.231216   48687 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
I0000 00:00:1691002191.521789   48541 soda_async_impl.cc:1128] SODA stopped processing audio, mics audio processed in millis: 6040, loopback audio processed in millis: 0
I0000 00:00:1691002191.521858   48541 soda_async_impl.cc:1140] Audio readers are stopped.
I0000 00:00:1691002191.521924   48541 terse_processor.cc:2561] Resetting Terse Processor with reason: 5
I0000 00:00:1691002191.521928   48541 terse_processor.cc:1502] Cancelling session.
W0000 00:00:1691002191.521995   48692 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522061   48693 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522079   48688 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522114   48691 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522148   48690 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522230   48683 cordz_functions.cc:53] RAW: Cordz disabled: not global symbol compliant
W0000 00:00:1691002191.522564   48541 decoder_endpointer_stream.cc:118] Acoustic ep reader thread cancelled.
I0000 00:00:1691002191.523332   48541 soda_async_impl.cc:1188] SODA session stopped due to: STOP_CALLED
I0000 00:00:1691002191.541937   48506 soda_async_impl.cc:1268] Deleted soda_impl.
[48461:4:0803/024951.545873:ERROR:mojo_audio_output_ipc.cc(186)] MojoAudioOutputIPC failed to acquire factory

```

---

### Post by TheFu on 2023-08-06
I don't know anything about this, but here's how I would proceed.

First, there are major differences between Google-Chrome and Chromium.  Google withholds some features from Chromium.  That would be the first thing I'd validate. Verify that Chromium isn't limited from doing this.  

Second, Chromium is distributed as a snap package on Ubuntu, so if you just say "install" it, you'll get the snap version with constraints. Often, those constraints break expected features. That would be the 2nd thing I checked.  If it should work and doesn't, look for work-arounds related to the snap packaging of Chromium.  If none exist, file a bug report with the Chromium package under Ubuntu.

If this stuff worked on 18.04 (pre-snap), I'd specifically mention that too.

---

