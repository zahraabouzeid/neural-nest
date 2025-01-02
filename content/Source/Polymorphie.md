Polymorphie bedeutet, dass Objekte unterschiedliche Gestalten annehmen können und sich unterschiedlich verhalten, je nach dem, wie sie aufgerufen werden. In Java basiert Polymorphie stark auf **Vererbung**, **Abstraktion** und **dynamischem Binden (late binding)**.

## Wichtigste Eigenschaften
Eine Referenz vom Typ der Basisklasse kann auf Objekte einer abgeleiteten Klasse zeigen.
```java
public static void main(String args [ ]){ 
  Mitarbeiter arbeiter, chef;
  arbeiter = new SchichtArbeiter();
  chef = new Manager(); 
}
```
4. **Late Binding**: Der konkrete Methodenausdruck wird erst zur Laufzeit entschieden.
## Abstrakte Klassen
Abstrakte Klassen dienen als Vorlage, die gemeinsame Eigenschaften und Methoden definiert, jedoch oft keine vollständige Implementierung enthält.

### Merkmale:
- **Abstrakte Methoden**: Methoden ohne Implementierung, die in abgeleiteten Klassen definiert werden müssen.
- **Keine Instanziierung**: Von abstrakten Klassen können keine Objekte erstellt werden.
- **Sinnvolle Verwendung**: Wenn für die Methode der Basisklasse kein allgemeiner Inhalt sinnvoll ist, z. B. eine `einkommen()`-Methode für alle Mitarbeiter.

### Beispiel:
```java
public abstract class Mitarbeiter {
    private String name;

    public abstract double einkommen(); // Abstrakte Methode
}

public class SchichtArbeiter extends Mitarbeiter {
    private double stundenSatz;
    private int stunden;

    @Override
    public double einkommen() {
        return stunden * stundenSatz;
    }
}
```

## Redefinition (Overriding)
- Eine Methode der Basisklasse wird in der abgeleiteten Klasse neu definiert.
- Dynamisches Verhalten: Der Methodenaufruf richtet sich nach der tatsächlichen Objektinstanz.

### Beispiel:
```java
public class Mitarbeiter {
    public String toString() {
        return "Mitarbeiter";
    }
}

public class SchichtArbeiter extends Mitarbeiter {
    @Override
    public String toString() {
        return "SchichtArbeiter";
    }
}
```

---

## Polymorphe Objekte
Ein polymorphes Objekt kann unterschiedliche Typen annehmen, abhängig von seiner Klasse und ihrer Vererbung.

### Eigenschaften:
- **Basisklassen-Referenzen**: Ermöglichen es, mit Objekten unterschiedlicher Typen einheitlich zu arbeiten.
- **Flexibilität**: Nur die Methoden der Basisklasse stehen zur Verfügung, außer bei Überschreibung.

### Beispiel:
```java
Mitarbeiter[] team = new Mitarbeiter[2];
team[0] = new SchichtArbeiter();
team[1] = new Manager();

for (Mitarbeiter m : team) {
    System.out.println(m.toString());
}
```
## Vorteile von Polymorphie und abstrakten Klassen
1. **Wartungsfreundlichkeit**: Neue Klassen können ohne große Änderungen hinzugefügt werden.
2. **Klarheit**: Vermeidung komplexer `if-else`-Strukturen.
3. **Code-Wiederverwendbarkeit**: Gemeinsame Funktionalität wird in Basisklassen definiert.

