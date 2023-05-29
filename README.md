# Expression to SQL String Converter
C# projesi, LINQ Expression'larını SQL sorgu dizesine dönüştürmeyi sağlayan BisExpression adındaki bir sınıfı ve ExpressionExtensions adlı genişletme sınıfını içerir. Bu iki sınıf, LINQ tabanlı sorgularınızı verimli ve hızlı bir şekilde SQL diline çevirmenize yardımcı olur.

# Anahtar Özellikler
* Geniş Expression tipleri desteği: Binary, Unary, Method Call, Lambda ve daha fazlasını destekler.
* Erişilebilir Member ve Constant Expressions: MemberExpression ve ConstantExpression türlerindeki değerlere erişim sağlar.
* SQL uyumlu string dönüşümü: Dönüştürülen ifadeleri doğrudan SQL sorgularında kullanabilirsiniz.

# Nasıl Çalışır
* BisExpression sınıfı ExpressionVisitor'ı genişletir ve farklı türdeki expression'ları işlemek üzere çeşitli Visit metodlarını override eder.
* BisExpression ayrıca, expression'ı ziyaret etmek ve üye erişimini ve sabit değerleri değiştirmek için bir ModifyExpression metodu içerir.
* ConvertExpressionToString metodu, belirli bir expression'ı alır ve desteklenen tiplere göre işlem yaparak bunu bir SQL sorgu dizesine çevirir.
* ExpressionExtensions genişletme sınıfı, genel LINQ Expression'larınızı hızlı ve kolay bir şekilde SQL sorgu dizesine dönüştürmenize yardımcı olur. Yalnızca ConvertExpressionToQueryString metodunu çağırmanız gerekir.

# Kullanım
* Bu GitHub deposunu klonlayın veya indirin.
* İndirdiğiniz dosyaları projenize ekleyin.

ExpressionExtensions sınıfını kullanmak için aşağıdaki örneği inceleyin:

```csharp
Expression<Func<MyType, bool>> myExpression = x => x.MyProperty == "MyValue";
string sqlQueryString = myExpression.ConvertExpressionToQueryString();
```csharp

Bu örnekte, myExpression adlı ifadenin SQL sorgu dizesini oluşturduk ve sqlQueryString değişkenine atadık.

# Dikkat Edilmesi Gerekenler
Bu kütüphanenin henüz desteklemediği bazı ExpressionType'lar ve MethodCallExpression metodları bulunmaktadır. Desteklenmeyen bir ifade kullanıldığında, çıktı string'i bir hata mesajı içerir. Bu sınıfların ileride daha fazla expression türünü ve metodu desteklemesi için geliştirme çalışmaları devam etmektedir.
