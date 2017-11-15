# textview-validator
This is for any class than inherits from TextView (Android)

### How to use
```
val tv:TextView = TextView()
val et:EditText = EditText()
val tv2:TextView = TextView()

``` 
-> Requirement.class 
* parameter *
Requirement(type:Int, alertMessage:String, maxChar : Int = 0, placeHolder:String = "")
```

val validator = MandatoryValidator()
                //if placeholder not set, and maxChar not set
                .add(tv, Requirement(MandatoryValidator.CANNOT_FILL_BLANK, "Cannot fill blank"))
                //if use placeholder as empty trigger
                .add(et, Requirement(MandatoryValidator.CANNOT_FILL_BLANK, "Tanggal akhir harus diisi", 0, "- / - / -"))
                //if use maxChar > 0
                .add(et, Requirement(MandatoryValidator.CANNOT_FILL_MORE_THAN_MAX, "Tidak boleh lebih dari 6 karakter", 6)
                .setListener(object : OnValidateFailed {
                    override fun didFailValidated(textView: TextView, alertMessage: String) {
                        showError(alertMessage)
                    }
                    
                    override fun didSuccess() {
                        //TODO: Success action
                    }
                })
                
//run validation
validator.validate()
```
