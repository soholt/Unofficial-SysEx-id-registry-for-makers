# Unofficial-SysEx-id-registry-for-makers
### To serve as a starting point for makers and to suggest some structure to custom SysEx messages..

There are a few reserved ranges in MIDI spec.:
* 0x7D Experimental or “Non-Commercial”, for internal use by research and educational institutions, and not in any products that are allowed to be released to the public.
and
* 0x60-7C [Reserved for Other Uses] - which seem to be heavily used by firmata

Firmata https://github.com/firmata/protocol/blob/master/protocol.md

#### Suggested structure..:
**DiyId** - claimed here via a pull request 1-127 [0x00 reserved for rolling, like midi manufacturers]

**PID** - product id, optional - if you are making more than 1 product 1-127 [0x00 reserved for rolling?]

**DeviceId** - optional - addressable, if chaining more than 1 device

**CMD & DATA** - up to the user

**SysEx msg:**
**F0 7D 7F DiyId PID DeviceId CMD DATA F7**
(it could also be 0x7E or 0x7D or ?? suggest)

Diy ID:
diy.json (Once 0x7F is reached, next diy vendor rolls over to be 0x00 0x01, same could be applied to PID etc)
``` json
{
    "0x00": { "0x01": "next id after parent reached 0x7F" },
    "0x01": "Lemons",
    "0x02": ""
}
```



Product ID
pid.json
``` json
{
    "0x01": { // <-- diy id
        "0x01": { "name": "Lemon-Midi-Roots", "text": "Midi Router", "url": "github/" } // <--  pid = Product Id
    },
    "0x02": {
        "0x01": { "txt": "", "text": "" }
    },
}
```

Maybe one day accepted by the MIDI

Run by makers

**Looking for good folk to accept pull requests**

Get USB PIDs here: https://pid.codes/howto/ from: https://hackaday.com/2015/04/03/usb-pids-for-all/
