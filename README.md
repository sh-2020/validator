��#validator

#validator

```
//创建一个规则对象

let rules = [{
                name: 'radio',
                rules: {required: true, message: '单选列表是必选项'},
            }, {
                name: 'checkbox',
                rules: {required: true, message: '多选列表是必选项'},
            }, {
                name: 'qq',
                rules: {required: true, message: 'qq必填'},
            }, {
                name: 'mobile',
                rules: [{required: true, message: 'mobile必填'}, {mobile: true, message: 'mobile格式不对'}],
            }, {
                name: 'vcode',
                rules: {match: true, message: '不同'},
            }, {
                name: 'idcard',
                rules: [{required: true, message: 'idcard必填'},{idcard:true,message:"身份证号码"}],
            }]
    //系统规则
<!--     "required":必填, "email" : 邮箱, "qq", "money", "url", "id", "lengthRange", "fixedLength", "payPwd", "notMatch", "match", "realname", "receiptname", "chinese", "safeAnswer", "alphanumeric", "idcard", "mobile", "phone", "areaPart", "phonePart", "year", "month", "day", "number", "notAllNum", "maxValue", "minValue", "integer", "rate", "minNumber","pwd","account"; -->
    //根据规则创建验证器
    const validate = new Validate(rules,data);
    //使用
    validate.check('idcard',"430524200102026637",(x)=>{  //x属于一个对象 {code:“验证状态”,msg:"错误信息" }
        console.log(x)
    })
    使用check函数 （支持Promise 对象）
    validate.check('idcard',"430524200102026637"）.then((obj)=>{
        console.log(obj)
    })
    // 自定义 验证器
     validate.customize("sss",function(value){   //value 传入的值
        console.log(value)
        return {
            code : 1,
            msg : "11111"
        }
    })
    //使用
     validate.check('sss',"430524200102026637",(x)=>{  //x属于一个对象 {code:“验证状态”,msg:"错误信息" }
        console.log(x)
    })

```
