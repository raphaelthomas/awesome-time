# Awesome Time [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of resources about time: definitions, standards, time zones,
calendars, atomic clocks, synchronization protocols, software, hardware, and
more.

## Contents

- [Definitions & Standards](#definitions--standards)
- [Leap Seconds](#leap-seconds)
- [Time Zones](#time-zones)
- [National Metrology Institutes](#national-metrology-institutes)
- [Network Time Protocol (NTP)](#network-time-protocol-ntp)
- [Precision Time Protocol (PTP)](#precision-time-protocol-ptp)
- [Time Synchronization Hardware](#time-synchronization-hardware)
- [Time-as-a-Service Providers](#time-as-a-service-providers)
- [Software Libraries](#software-libraries)
- [Security Research](#security-research)
- [Operational Guides & Best Practices](#operational-guides--best-practices)
- [Books, Papers & Long-form Reading](#books-papers--long-form-reading)
- [Talks](#talks)
- [Communities & Projects](#communities--projects)

## Definitions & Standards

- [UTC (Coordinated Universal Time)](https://www.bipm.org/en/time-metrology) -
Maintained by the BIPM from a weighted average of atomic clocks worldwide.
- [TAI (International Atomic Time)](https://www.bipm.org/en/bipm-services/timescales/tai.html) -
The continuous atomic timescale underlying UTC.
- [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) - Date
and time representation standard.
- [RFC 3339](https://www.rfc-editor.org/rfc/rfc3339) - Internet date/time
format profile of ISO 8601.
- [Time standard](https://en.wikipedia.org/wiki/Time_standard#Current_time_standards) -
Wikipedia overview of the timescales in current use.

## Leap Seconds

- [Leap second](https://en.wikipedia.org/wiki/Leap_second) - Wikipedia
overview of why and how leap seconds are inserted.
- [IERS Bulletin C leap second data](https://hpiers.obspm.fr/eop-pc/earthor/utc/leapsecond.html) -
Historical record of leap second announcements.
- [There's a Growing Crisis Over the Leap Second](https://www.nature.com/articles/d41586-022-03783-5) -
Nature on the 2022 vote to abandon the leap second by 2035.
- [Leaping seconds](https://dotat.at/@/2022-12-04-leap-seconds.html) - Tony
Finch (tzdata/NTP Pool contributor) on the mechanics and politics of leap
seconds.
- [The Leap Second Behaviour of NTP Servers](https://tma.ifip.org/2016/papers/tma2016-final27.pdf) -
TMA 2016 measurement study of how real NTP servers handle leap seconds.
- [It's Time to Leave the Leap Second in the Past](https://engineering.fb.com/2022/07/25/production-engineering/its-time-to-leave-the-leap-second-in-the-past/) -
Meta engineering's case for smearing leap seconds instead of stepping them.

## Time Zones

- [IANA Time Zones Database (tzdata)](https://www.iana.org/time-zones) - The
canonical source of timezone rules used by nearly every OS and language.
  - [Sources and Links](https://www.iana.org/time-zones/tz-link) -
  community-contributed content contained in the time zone database.
  - [tz database background (theory.html)](https://data.iana.org/time-zones/theory.html) -
  How timezone rules and historical edge cases are decided.
- [Working with Time Zones](https://www.w3.org/TR/timezone/) - W3C note on
correctly handling time zones and offsets on the web.

## National Metrology Institutes

- [METAS (Swiss Federal Institute of Metrology)](https://www.metas.ch/) -
Swiss national time and frequency standard.
- [NIST Time and Frequency Division](https://www.nist.gov/pml/time-and-frequency-division) -
US civilian time standard, including the NIST-F2 cesium fountain clock.
- [PTB (Physikalisch-Technische Bundesanstalt)](https://www.ptb.de/cms/en.html) -
German national metrology institute, atomic clock research.

## Network Time Protocol (NTP)

### IETF Request for Comments (RFCs)

- [RFC 5905](https://datatracker.ietf.org/doc/html/rfc5905) - Network Time
Protocol Version 4: Protocol and Algorithms Specification
- [RFC 8573](https://www.rfc-editor.org/rfc/rfc8573) - Message Authentication
Codes for the Network Time Protocol
- [RFC 8915](https://datatracker.ietf.org/doc/html/rfc8915) - Network Time
Security for the Network Time Protocol
- [RFC 9109](https://datatracker.ietf.org/doc/html/rfc9109) - Network Time
Protocol Version 4: Port Randomization
- [RFC 9769](https://datatracker.ietf.org/doc/html/rfc9769) - NTP Interleaved
Modes
- [Network Time Protocol Version 5 (draft)](https://datatracker.ietf.org/doc/draft-ietf-ntp-ntpv5/)

### Software Implementations

- [`ntpd`](https://www.ntp.org/)
- [Chrony](https://chrony-project.org/) - Modern NTP/PTP client and server;
`hwtimestamp`, interleaved mode, `prefer`/`require` directives.
- [NTPsec](https://www.ntpsec.org/) - Security-hardened fork of the reference
NTP implementation.
- [`ntpd-rs`](https://github.com/pendulum-project/ntpd-rs) - Rust NTP
implementation with NTS support.
- [facebook/time](https://github.com/facebook/time) - Meta's Go NTP/PTP
implementation, used by its own time infrastructure.

### Monitoring & Tooling

- [chrony_exporter](https://github.com/superq/chrony_exporter) - Prometheus
exporter for chrony tracking stats.
- [meinberg_ltos_exporter](https://github.com/raphaelthomas/meinberg_ltos_exporter) -
Prometheus exporter for Meinberg LANTIME (LTOS) appliances.
- [ntpmon](https://github.com/paulgear/ntpmon) - NTP/chrony health monitor
with Nagios checks and Prometheus/Telegraf output.
- [`TIME.md`](https://github.com/prometheus/node_exporter/blob/master/docs/TIME.md) -
node_exporter's notes on measuring clock sync/drift correctly.
- [Understanding `reach`](https://www.satsignal.eu/ntp/reach.html) - How
NTP's 8-bit reach shift register reports poll success/failure.

## Precision Time Protocol (PTP)

- [IEEE 1588](https://standards.ieee.org/ieee/1588/6825/) - Precision Time
Protocol for sub-microsecond synchronization.
- [ITU-T G.8275.1/.2](https://www.itu.int/rec/T-REC-G.8275.1/en) - Telecom
profiles for PTP (phase/time distribution).
- [`ptp4l` / linuxptp](https://linuxptp.sourceforge.net/) - Linux PTP
implementation, often paired with `phc2sys`.

## Time Synchronization Hardware

- [Meinberg LANTIME](https://www.meinbergglobal.com/english/products/) -
GPS/GNSS timeservers, Stratum 1 appliances.
- [Microchip/Symmetricom TimeProvider](https://www.microchip.com/) -
Grandmaster clocks for telecom-grade PTP.
- [u-blox ZED-F9T](https://www.u-blox.com/en/product/zed-f9t-module) -
Timing-focused GNSS module.

## Time-as-a-Service Providers

- [AWS Time Sync Service](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/set-time.html)
- [Cloudflare Time Services](https://www.cloudflare.com/en-gb/time/)
- [Google Public NTP](https://developers.google.com/time/)
- [Meta's open-source Time Appliance](https://engineering.fb.com/2021/08/11/open-source/time-appliance/) -
Meta's Stratum 1 hardware/firmware, released as an OCP Time Appliance.

## Software Libraries

- [chrono (Rust)](https://github.com/chronotope/chrono) - Date and time
library for Rust.
- [java.time](https://docs.oracle.com/javase/8/docs/api/java/time/package-summary.html) -
Modern Java date/time API (JSR-310).
- [Python `zoneinfo`](https://docs.python.org/3/library/zoneinfo.html) -
Standard library IANA timezone support.
- [Temporal (JS)](https://tc39.es/proposal-temporal/) - TC39 proposal aiming
to fix JavaScript's `Date` problems.

## Security Research

- [Sharon Goldberg — NTP security publications](https://www.cs.bu.edu/~goldbe/pub-index.html) -
Research on NTP protocol vulnerabilities, including off-path and
authenticated-broadcast attacks.
- [The Security of NTP's Datagram Protocol](https://eprint.iacr.org/2016/1006.pdf) -
Malhotra & Goldberg, FC'17: formal analysis of NTP's on/off-path threat model.
- [Preventing (Network) Time Travel with Chronos](https://www.ndss-symposium.org/wp-content/uploads/2018/02/ndss2018_02A-2_Deutsch_paper.pdf) -
Deutsch et al., NDSS'18: a client-side defense against time-shifting attacks.
- [Taming the 800 Pound Gorilla: The Rise and Decline of NTP DDoS Attacks](https://conferences2.sigcomm.org/imc/2014/papers/p435.pdf) -
Czyz et al., IMC'14: measurement study of the 2014 NTP amplification wave.
- [On Borrowed Time: Measurement-Informed Understanding of the NTP Pool's Robustness to Monopoly Attacks](https://www.ndss-symposium.org/wp-content/uploads/2026-f541-paper.pdf) -
Beverly & Rye, NDSS'26: shows a handful of malicious servers could capture
most NTP Pool traffic in many countries.
- [Network Time Security (NTS): Updated Security for NTP](https://blog.meinbergglobal.com/2021/07/14/network-time-security-nts-updated-security-for-ntp/) -
Meinberg's overview of what NTS actually fixes.
- [NTS Whitepaper](https://www.netnod.se/sites/default/files/2021-01/Netnod_NTS_Whitepaper_2020.pdf) -
Netnod's introduction to Network Time Security concepts and deployment.

## Operational Guides & Best Practices

- [Best Practices for NTP Services](https://insights.sei.cmu.edu/blog/best-practices-for-ntp-services/) -
Carnegie Mellon SEI on running NTP securely and reliably.
- [Best Practices for Connecting to NTP Servers](https://labs.ripe.net/author/christer-weinigel/best-practices-for-connecting-to-ntp-servers/) -
RIPE Labs on picking and configuring upstream time sources.
- [Time Synchronization Errors Caused by Network Asymmetries](https://kb.meinbergglobal.com/kb/time_sync/time_synchronization_errors_caused_by_network_asymmetries) -
Meinberg KB on why asymmetric network paths degrade NTP accuracy.
- [Time Synchronization in Virtual Machines](https://kb.meinbergglobal.com/kb/time_sync/time_synchronization_in_virtual_machines) -
Meinberg KB on the pitfalls of keeping time inside VMs.
- [Real Life NTP](https://pthree.org/2013/11/05/real-life-ntp/) - Practical
walkthrough of configuring a resilient NTP hierarchy.
- [The School for Sysadmins Who Can't Timesync Good](https://www.libertysys.com.au/2016/09/the-school-for-sysadmins-who-cant-timesync-good-and-wanna-learn-to-do-other-stuff-good-too-part-1-the-problem-with-ntp/) -
Five-part practical series on diagnosing and fixing NTP in the real world.

## Books, Papers & Long-form Reading

- [A Brief History of NTP Time: Confessions of an Internet Timekeeper](https://www.eecis.udel.edu/~mills/database/papers/history.pdf) -
David L. Mills on the origins and evolution of NTP.
- [Maintaining the Time in a Distributed System](https://dl.acm.org/doi/pdf/10.1145/800221.806730) -
Marzullo & Owicki, PODC'83: the algorithm behind NTP's clock selection.
- [A Survey of the NTP Network](https://www.eecis.udel.edu/~mills/database/reports/ntp-survey99-minar.pdf) -
Nelson Minar, 1999: an early Internet-wide crawl of NTP topology and health.
- [The Thorny Problem of Keeping the Internet's Time](https://www.newyorker.com/tech/annals-of-technology/the-thorny-problem-of-keeping-the-internets-time) -
The New Yorker profiles the NTP Pool and the people who keep it running.
- [Weberblog.net NTP series](https://weberblog.net/ntp/) - Multi-part deep
dive into NTP internals and packet analysis.
- ["Leaping Seconds"](http://ipj.dreamhosters.com/wp-content/uploads/issues/2012/ipj15-3.pdf) -
The Internet Protocol Journal, vol. 15, no. 3 (Sep 2012).
- ["Network Time Protocol"](http://ipj.dreamhosters.com/wp-content/uploads/issues/2012/ipj15-4.pdf) -
The Internet Protocol Journal, vol. 15, no. 4 (Dec 2012).

## Talks

- ["UTC is Enough for Everyone, Right?"](https://zachholman.com/talk/utc-is-enough-for-everyone-right) -
Zach Holman's talk on the countless ways time zone handling goes wrong.

## Communities & Projects

- [NTP Pool Project](https://www.ntppool.org/)
- [NTP Pool community forum](https://community.ntppool.org)
- [ntp.org](https://www.ntp.org/)
- [IANA tz mailing list](https://www.iana.org/time-zones)

## Contributing

Contributions welcome - see [CONTRIBUTING.md](CONTRIBUTING.md).
