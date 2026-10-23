# Rammer for Topp-Trollet

Dette er reglene spillet må holde seg innenfor. Bruk listen som sjekkliste før lansering, og når noen vil legge til noe nytt.

Regler som påvirker spillmekanikken ligger i `RULES` i `index.html`. Kommentarene der peker tilbake hit med regelnummeret (R1, R2 og så videre).

Listen er ikke en juridisk vurdering. Markedsføringen bør vurderes av juridisk kompetanse før lansering.

## Sikkerhetsråd som styrer spillmekanikken

### R1 Hvitevarer går bare når noen er hjemme og våkne

- **Regel:** Vaskemaskin, tørketrommel og oppvaskmaskin kan bare legges mellom kl. 16 og 23. Oppvasken kan tidligst starte kl. 18, etter middag. Spillet skal aldri belønne at hvitevarer går om natta eller mens huset er tomt.
- **Kilde:** Brannvernråd fra DSB og Norsk brannvernforening: ikke la vaskemaskin, tørketrommel eller oppvaskmaskin gå når du sover eller ikke er hjemme. Se [dsb.no](https://www.dsb.no) og [brannvernforeningen.no](https://www.brannvernforeningen.no).
- **I koden:** `RULES.awake` og `RULES.dishFrom`

### R2 Elbilen lader med fast ladeboks

- **Regel:** Spillet viser lading fra ladeboks i garasjen. Det skal aldri vise eller belønne lading fra vanlig stikkontakt.
- **Kilde:** DSB anbefaler fast installert ladepunkt (ladeboks) for regelmessig lading av elbil. Se [dsb.no](https://www.dsb.no).
- **I koden:** `RULES.car`. Teksten «Ladeboks i garasjen» står på elbilraden.

### R3 Ladeeffekten må være realistisk for boligen

- **Regel:** 11 kW-lading vises med en fotnote om at det krever et 400 V-anlegg. Mange eldre hus har 230 V IT-nett og maks rundt 7,4 kW.
- **Kilde:** Vanlig elinstallasjonspraksis. En elektroinstallatør bør bekrefte formuleringen før lansering.
- **I koden:** `RULES.chargers` og fotnoten under ladevalgene.

## Lover og regler som styrer reklamen

### R4 Ingen villedende spareberegninger

- **Regel:**
  - Alle priser og kapasitetstrinn skal være merket som forenklede eksempler.
  - Sparetall med fjernvarme skal si at fjernvarmen har sin egen pris.
  - Spillet skal si at fjernvarme krever vannbåren varme og at boligen ligger i fjernvarmeområdet.
- **Kilde:** Markedsføringsloven (LOV-2009-01-09-2), forbudet mot villedende handelspraksis. Se [lovdata.no](https://lovdata.no/dokument/NL/lov/2009-01-09-2).
- **I koden:** Fotnoten under spillet og teksten i resultatet etter dag 2.

### R5 Varsomhet overfor barn

- **Regel:** Et tegnet troll appellerer til barn. Spillet skal ikke oppfordre direkte til kjøp. «Les om fjernvarme» er en lenke til informasjon, ikke en bestillingsknapp.
- **Kilde:** Markedsføringsloven har strengere regler for handelspraksis overfor barn. Se [Forbrukertilsynet](https://www.forbrukertilsynet.no).
- **I koden:** Lenken i resultatet etter dag 2.

### R6 Universell utforming

- **Regel:** Alt som kan gjøres med mus eller finger, skal også kunne gjøres med tastatur. Elementene skal ha tekstalternativ. Ingen informasjon skal formidles bare med farge.
- **Kilde:** Likestillings- og diskrimineringsloven og forskrift om universell utforming av IKT-løsninger, som stiller WCAG-krav. Se [uutilsynet.no](https://www.uutilsynet.no).
- **Status:** Blokkene kan flyttes med piltastene, og huset og blokkene har tekstalternativ. Spillet er ikke testet med skjermleser.

### R7 Personvern og informasjonskapsler

- **Regel:**
  - Ingen innhold fra tredjepart lastes uten samtykke.
  - Fonten ligger i repoet (`fonts/`), ikke hos Google Fonts, fordi Google Fonts sender brukerens IP-adresse til Google.
  - Analyseverktøy som Google Analytics eller Meta Pixel krever samtykkeløsning før de kan legges inn.
- **Kilde:** Ekomloven (krav om samtykke til informasjonskapsler) og personvernforordningen (GDPR).
- **I koden:** `@font-face` øverst i stilarket.

## Rammer vi har satt selv

### R8 Ingen ekte selskaper som skurker

- **Regel:** Skurken er det fiktive Topp-Trollet, ikke et nettselskap. Ekte selskapsnavn og ekte tariffer skal ikke brukes.
- **I koden:** `STEPS`, `spot` og `gridFee` er oppdiktede, typiske tall.

### R9 Grafisk profil

- **Regel:** Farger og font skal følge Bodø Energis designmanual.
- **Mangler:** Tekstplassholderen nederst til høyre må byttes med den offisielle logofilen for Bodø Energi Varme før lansering.

### R11 Rettferdig sammenligning mellom fjernvarme og varmepumpe

- **Regel:** Spillet sammenligner fjernvarme med en luft-vann-varmepumpe, fordi begge krever vannbåren varme. Da blir premisset likt. Varmepumpen får realistiske, ikke svake, tall. Sparetallet skal nevne at varmepumpen koster å kjøpe og installere, slik det nevner prisen på fjernvarme. Dag 2 vurderes mot beste mulige løsning for hver oppgradering, slik at ingen av dem er umulig å vinne.
- **Antakelse:** Effektfaktoren (COP) er 2,5 for oppvarming og 2,0 for varmtvann en vinterdag i Bodø. Årsgjennomsnittet (SCOP) er ofte rundt 3, men det er lavere når det er kaldt og når vannet skal holde dusjtemperatur. Tallene bør kvalitetssikres av en fagperson.
- **Kilde:** Markedsføringsloven krever at sammenligninger er objektive og etterprøvbare.
- **I koden:** `RULES.heatPump`, `MODES` og `starsFor`

### R10 Faktiske data der de finnes

- **Regel:** Når spillet viser noe fra virkeligheten, skal det bygge på ekte data.
- **I dag:** Soltidene er for Bodø 17. november fra MET Sunrise 3.0: sola står opp 09:13 og går ned 14:20. Solbuen er tegnet høyere enn de faktiske 3,7 grader, slik at sola synes over huset.
