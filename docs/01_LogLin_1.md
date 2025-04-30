---
title: "Kapitel 1"
author: "W. R. Gruber"
date: 'r sysdate()'
output: 
  html_document:
    code_folding: hide
    number_sections: yes
    toc: yes
    toc_float: yes
---



# Motivation {-}

Die logistische Regression ist ein Spezialfall der Regressionsanalyse und wird verwendet, wenn die abhängige Variable nominalskaliert ist. In der Psychologie kann dies beispielsweise bei der Variable "Therapieerfolg" zutreffend sein, mit den Ausprägungen "Erfolg" und "keinen Erfolg".

Die logistische Regressionsanalyse stellt somit das Gegenstück zur linearen Regression dar, bei der die abhängige Variable des Regressionsmodells zumindest intervallskaliert sein muss.

Mit der logistischen Regression können wir nun die abhängige Variable erklären bzw. die Eintrittswahrscheinlichkeit der Ausprägungen dieser Variable schätzen.

## Beispiel aus der Psychologie

- Du möchtest untersuchen, ob eine bestimmte Therapieform für Patienten mit einer Angststörung erfolgreich ist. Hierzu erhältst du einen Datensatz mit Informationen über Patienten, die eine Therapie durchlaufen haben, sowie deren Therapieergebnisse (erfolgreich/nicht erfolgreich).

- Ein anderes Beispiel könnte darin bestehen, die Wahrscheinlichkeit abzuschätzen, ob eine Person mit einem hohen Maß an Stress und bestimmten Persönlichkeitsmerkmalen "anfällig" oder "nicht anfällig" für Burnout ist. Hierfür könntest du Daten über Stresslevel, Persönlichkeitstests und den aktuellen psychischen Zustand der Personen verwenden.

# Grundlegende Idee der logistischen Regression {-}



Im Unterschied zur bekannten linearen Regression, werden also anstatt stetiger Werte nun diskrete Werte ausgegeben. In der einfachsten Form der logistischen Regression können somit dichotome Variablen (0 oder 1) prognostiziert werden.

Hierfür wird die Wahrscheinlichkeit für das Eintreten der Ausprägung 1 (= Merkmal vorhanden) geschätzt. 

In der Psychologie ist es einerseits von Interesse herauszufinden, welche Variablen einen Einfluss auf z.B. ein bestimmtes Persönlichkeitsmerkmal haben. Andererseits ist es auch wichtig zu entscheiden, ab wann es zu einer bedeutsamen Abweichung von einem bestimmten Normbereich kommt.  Für diesen Fall könnte dann 0 für "kein Problem" und 1 für "problematisch" stehen. 

Wir werden nun mit Hilfe der logistischen Regression den Einfluss verschiedener Faktoren für folgende Fragestellung überprüfen und uns dabei die Eigenschaften der logistischen Regression erarbeiten.

Als Mitarbeiter einer groß angelegten Schlafstudie haben Sie die Aufgabe, die Faktoren, die zu Schlafstörung führen, besser zu verstehen. Außerdem möchten Sie dieses Wissen nutzen, um bei Vorliegen einer Schlafstörung eingreifen und die Gesundheit und Lebensqualität dieser Personen verbessern zu können. Sie möchten also die Wahrscheinlichkeit vorhersagen können, dass eine Person mit bestimmten Merkmalen eine Schlafstörung hat.

Folgende Daten[^1] liegen für Ihre Analysen vor:

[^1]: bei den vorliegenden Daten handelt es sich um simulierte Daten!

- `sleep_problem`: gibt an, ob eine Person ein Schlafproblem hat (1 = ja; 0 = nein)
- `coffee_drinker`: gibt an, ob eine Person regelmäßig Kaffee trinkt (1 = ja, Kaffeetrinker; 0 = kein Kaffeetrinker)
- `fast_food_spend`: jährlichen Ausgaben für Fast Food
- `income`: das Jahreseinkommen

Dieser Datensatz steht im Blackboard zum Download zur Verfügung (*sleep_data.csv*).


