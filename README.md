# Simulcast Sandbox

Test application for video capture and related WebRTC APIs.

## How to use

1. Allow the page to access your capture devices.
2. Configure the encoders.
2. Press the Start button.

## Capture configuration

The application supports the following options:
- Default or specific device usage (getUserMedia only)
- Capture resolution (getUserMedia / getDisplayMedia)
- Capture framerate
- [Content Hint](https://developer.mozilla.org/en-US/docs/Web/API/MediaStreamTrack/contentHint)

## Encoder configuration

### Global configuration

- Transceiver: Codec will be placed first using setCodecPrerences.
- Simulcast
  - Add / Remove layer: Add or remove a simulcast layer.
  - Layers
    - Merged: SDP offers and answers are not modified.
    - Split: simulcast layers split into multiple video streams (achieved by swapping MID and RID RTP header extension and recreating the SDP offer and answers).
  - Degradation Preference

### Per-encoder configuration

- [Codec](https://w3c.github.io/webrtc-pc/#dom-rtcrtpencodingparameters-codec): Which codec to use for the stream. The codec list is derived from the encoder capabilities.
- [maxBitrate](https://w3c.github.io/webrtc-pc/#dom-rtcrtpencodingparameters-maxbitrate): Maximum bitrate to use for the stream, unit is bit per second.
- [scaleResolutionDownBy](https://w3c.github.io/webrtc-pc/#dom-rtcrtpencodingparameters-scaleresolutiondownby): Scaling factor
- [maxFramerate](https://w3c.github.io/webrtc-pc/#dom-rtcrtpencodingparameters-maxframerate): Maximum framerate for the stream.
- [scalabilityMode](https://w3c.github.io/webrtc-svc/#dom-rtcrtpencodingparameters-scalabilitymode): Scalability mode used by the stream. No checks are made to ensure that only relevant modes are listed. Requires support of the `webrtc-svc` specification.
- [active](https://w3c.github.io/webrtc-pc/#dom-rtcrtpencodingparameters-active): Enable the stream.
- [priority](https://w3c.github.io/webrtc-priority/#dom-rtcrtpencodingparameters-priority): Bandwidth allocation priority for the stream.

## Statistics

Statistics reported for each stream are available by expanding the `Encoder stats` details in each layer configuration box.

## Recording

A red button to start recording is available with each received stream video element.
The video is recorded using the MediaRecoder API.

A list of recordings appears at the bottom of the page with download links for each.
Recordings are local and will be lost when refreshing the page.
